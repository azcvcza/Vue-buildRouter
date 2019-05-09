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
      currentView:{}
    }
  },
  created() {
    if (this.getRouteObject() === undefined) {
      this.currentView = {
        template: `
          <h3 class="subtitle has-text-white">
            Not Found :(. Pick a Pokémon from the list below!
          </h3>
        `
      };
    } else {
      this.currentView = this.getRouteObject().component;
    }
  },
  methods: {
    getRouteObject() {
      return routes.find(
        route => route.path === window.location.pathname
      );
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
