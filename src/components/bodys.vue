<template>
    <div class="bodys">
        <table class="date">
            <thead>
                <tr>
                    <th class="head" v-for="{week,id} in week">{{week}}</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>
                        <div>
                            <span>11</span>
                            <span>初一</span>
                        </div>
                    </td>
                    <td>
                        <div>
                            <span>11</span>
                            <span>初一</span>
                        </div>
                    </td>
                    <td>
                        <div>
                            <span>11</span>
                            <span>初一</span>
                        </div>
                    </td>
                    <td>
                        <div>
                            <span>11</span>
                            <span>初一</span>
                        </div>
                    </td>
                    <td>
                        <div>
                            <span>11</span>
                            <span>初一</span>
                        </div>
                    </td>
                    <td>
                        <div>
                            <span>11</span>
                            <span>初一</span>
                        </div>
                    </td>
                    <td>
                        <div>
                            <span>11</span>
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
            week:[
                {id:1,week:'一'},
                {id:2,week:'二'},
                {id:3,week:'三'},
                {id:4,week:'四'},
                {id:5,week:'五'},
                {id:6,week:'六'},
                {id:7,week:'七'},
            ]
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
</style>