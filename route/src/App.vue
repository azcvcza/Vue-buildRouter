<template>
  <div id="app">
    <img src="./assets/logo.png">
    <router-view/>
  </div>
</template>

<script>
import A from './components/A'
import B from './components/B'
import C from './components/C'
//import View from './components/View'
const routes =[
  {path:'/',component:A},
  {path:'/A',component:A},
  {path:'/B',component:B},
  {path:'/C',component:C},  
];
const View ={
  name:'router-view',
  template:`<component :is=currentView></component>`,
  data:()=>{
    return {
      currentView:A
    }
  }
}
export default {
  name: 'App',
  components: {
    'router-view':View
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
