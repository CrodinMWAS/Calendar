<template>
  <div id="content">
    <h1>Your Calendar</h1>
    <div id="calendar">
      <div id="day" v-for="day in days" @click="day.opened = !day.opened"> 
        <h1 v-if="!day.opened" >{{ day.dayId }}</h1> 
        <div id="bottomDoor" v-if="!day.opened" ><div id="doorKnob"></div></div> 
        <div id="prize" v-if="day.opened"><h1>{{ day.message }}</h1></div>
      </div>
    </div>
  </div>
</template>

<script>
export default{
  methods:{
    fillDays(){
      for (let i = 1; i != 25; i++) {
        this.days.push({dayId: i, message: `Its dec ${i}`, opened: false})
      }
    }
  },
  mounted: function(){
    this.fillDays()
  },
  data(){
    return{
      days: [ ],
    }
  }
}
</script>

<style>
#app{
  margin: 0;
  padding: 0;
}
#content{
  width: 100vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
#calendar{
  width: 75%;
  height: 75%;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 5%;
  background-color: darkgreen;
}
#day{
  width: 15vw;
  height: 15vw;
  margin: 5% 0;
  background-color: red;
  box-sizing: border-box;
  transition: all 0.2s ease-in-out;
  position: relative;
}
#day:hover{
  cursor: pointer;
  scale: 1.2;
  box-shadow: 0 0 50px grey;
}
#bottomDoor{
  width: 100%;
  height: 50%;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}
#doorKnob{
  width: 60px;
  height: 20px;
  background-color: black;
  border-radius: 25px;
  margin: 20px;
}
#prize{
  width: 100%;
  height: 100%;
  outline: 2px solid black;
  position: absolute;
  top: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>