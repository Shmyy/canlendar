<template>
    <div class="bodys">
        <table class="date">
            <thead>
                <tr>
                    <th class="head" v-for="(item,index) in dayname">{{item}}</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(week,index) in theweek()">
                    <td v-for="(day,index2) in week">
                        <div>
                            <span>{{day}}</span>
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
            // year:2022,
            // 月（从0到11，总共12个月）
            month:4
        }
    },
    mounted(){
        var day = []
        // 获取这个月第一天是星期几？
        var themoon_1stday = (new Date(this.year,this.month-1,1)).getDay()
        // 本月有多少天？
        // 
        console.log(themoon_1stday)
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
    border:solid 1px  black; 
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

.date .holiday{

}
</style>