<template>
    <div class="bodys">
        <table class="date">
            <thead>
                <tr>
                    <th class="head" v-for="(item,index) in dayname">{{item}}</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(week,index) in theweek()" v-if="day[0]">
                    <td v-for="(day,index2) in week" :class="{'not_themonth':day.premonth || day.nextmonth}">
                        <div>
                            <span>{{day.days}}</span>
                            <span>初一</span>
                        </div>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    name: 'bodys',
    data(){
        return {
            dayname:['一','二','三','四','五','六','七'],
            day:[],
            // 年
            year:2022,
            // 月（从0到11，总共12个月）
            month:4
        }
    },
    mounted(){
        var day = []
        
        // 1.获取这个月第一天是星期几？
        var themonth_1stday = (new Date(this.year,this.month-1,1)).getDay()
        
        // 2.本月有多少天？
        // 此时经典算法是判断这个月是不是1、3、5、7、8、10、12，那么就是31天，
        //    ，4、6、9、11就是30天，2月份需要看是不是闰年

        // 这个月的最后一天就是下个月的第一天减1毫秒的那天(可以知道有多少天)
        var y = this.month == 12 ? this.year + 1 : this.year
        var m = this.month == 12 ? 1 : this.month
        // 日期对象减去常数表示得到时间戳，减去1表示减去1毫秒
        var themonth_allday = new Date(new Date(y,m,1) - 1).getDate()
    
        // 3.上个月的最后一天是几号（同时可以知道上个月有多少天）
        // 即这个月的第一天减去1毫秒所在的天
        var prevmonth_lastdate = new Date(new Date(this.year,this.month - 1,1) - 1 ).getDate()

        // 4.这个月的第一天是星期几，就要放入几个上个月的尾巴
        while(themonth_1stday--){
            day.unshift({"days":prevmonth_lastdate--,"premonth": true})

        }
        // 5.放置本月的日期
        var count = 1
        while(themonth_allday-- > 0){
            day.push({"days":count++,"themonth":true})
        }
        // 6.补足42项（一个日历有42个格子）
        var c = 42 - day.length
        var count2 = 1
        while(c-- > 0){
            day.push({"days":count2++,"nextmonth":true})
        }
        // console.log(day)

        this.day = day

    },
    methods:{
        // 返回第n周的日期序列，序号从0开始
        theweek:function(){
            // console.log(n)
            var day_arr = []
            for(var i=0;i<6;i++){
                var week_arr = []
                for(var j=0;j<7;j++){
                    week_arr.push(this.day[i*7 + j])
                }
                day_arr.push(week_arr)
            }
            return day_arr
        }
    }
}
</script>


<style scoped>
.bodys{
    flex: 4;
    /* background-color: green; */
    /* border:solid 1px  black;  */
}
.date{
    width: 100%;

    border-spacing: 4px;
}

.date th{
    height: 35px;
    font-weight: normal;
}

.date td{
    width: 60px;
    height: 60px;
    
}
.date div{
    height: 100%;
    box-sizing: border-box;
    border-radius: 6px;
    border: 2px solid transparent;
    cursor: pointer;

    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    /* background-color: #ccc; */
}

.date div:hover,.date div.active{
    border-color: #bdbfc8;
}

.date div span:nth-child(1){
    font-size: 18px;
    font-weight: 900;
    color: #000;
}
.date div span:nth-child(2){
    font-size: 12px;
    font-weight: 500;
    color: #333;
}

.date td:nth-child(n+6) span:nth-child(1){
    color: #f73131;
}

.not_themonth{
    opacity: .4;
}
</style>