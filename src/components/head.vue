<template>
<div class="heads">

  <div class="year_select">
    <select name="" id="select1">
      <option value="">年份</option>
      <option v-for="(years,id) in year_data" :key="id" :value="years.id">
        {{years.year}}
      </option>
    </select>
  </div>

  <div class="moon_select">
    <div class="choose" type="button">&lt;</div>
    <select name="" id="select2">
      <option value=""></option>
      <option v-for="(moons,id) in moon_data" :key="id" :value="moons.id">
        {{moons.moon}}
      </option>
    </select>
    <div class="choose">&gt;</div>
  </div>

  <div class="plan">
    <select name="" id="select3">
      <option value="">安排</option>
      <option v-for="(plans,id) in plan_data" :key="id" :value="plans.id">
        {{plans.plan}}
      </option>
    </select>
  </div>

  <div class="today">
    <button class="btn_today">返回今天</button>
  </div>
</div>
</template>

<script>
export default {
  name: 'heads',
  data(){
    return{
      year_data:[
        {id:1,year:2022},
        {id:2,year:2021},
        {id:3,year:2020},
        {id:4,year:2019}
      ],
      moon_data:[
        {id:1,moon:'1月'},
        {id:2,moon:'2月'},
        {id:3,moon:'3月'},
        {id:4,moon:'4月'},
        {id:5,moon:'5月'},
      ],
      plan_data:[
        {id:1,plan:'元宵'}
      ]
    }
  }
}
</script>


<style scoped>
.heads{
  flex: 1;
  display: flex;

  /* background-color: blue; */
  /* border:solid 1px  black;  */
}

.year_select{
  flex: 1;

  display: flex;
  align-items: center;
  justify-content: space-around;

  /* background-color: blue; */
}
#select1{
  width: 96px;
  height: 28px;
  padding: 0 7px;
}

.moon_select{
  flex: 1.5;

  display: flex;
  align-items: center;
  justify-content: space-around;

  /* background-color: red; */
}
#select2{
  width: 96px;
  height: 28px;
  padding: 0 7px;
}
.choose{
  font-size: 25px;
  font-weight: 800;
  cursor: pointer;
}




.plan{
  flex: 1;

  display: flex;
  align-items: center;
  justify-content: space-around;

  /* background-color: green; */
}
#select3{
  width: 86px;
  height: 28px;
  padding: 0 7px;
}

.today{
  flex: 1;

  display: flex;
  align-items: center;
  justify-content: space-around;

}
.btn_today{
  width: 86px;
  height: 28px;
}
</style>
