<template>
	<div id="app">
    <div class="container">
      <img src="./assets/logo.png">
			<div class="items">
				<router-link to="/A"></router-link>
			</div>
			<div class="items">
				<router-link to="/B"></router-link>
			</div>
			<div class="items">
				<router-link to="/C"></router-link>
			</div>
		</div>
		
		<router-view/>
		
	</div>
</template>

<script>
  import Vue from 'vue'
  //
	import A from "./components/A";
	import B from "./components/B";
	import C from "./components/C";
  //import View from './components/View'
  //build Event Bus
  const EventBus = new Vue();
	//View
	const View = {
		name: "router-view",
		template: `<component :is=currentView></component>`,
		data: () => {
			return {
				currentView: {}
			};
		},
		created() {
			if (this.getRouteObject() === undefined) {
				this.currentView = {
					template: `
		          <h3 class="subtitle has-text-white">
		            Not Found : no exact page
		          </h3>
		        `
				};
			} else {
				this.currentView = this.getRouteObject().component;
      }
      EventBus.$on('navigate',()=>{
        this.currentView = this.getRouteObject().component;
      })
		},
		methods: {
			getRouteObject() {
				return routes.find(route => route.path === window.location.pathname);
			}
		}
	};
	//
	//Link
	const Link = {
		name: "router-link",

		props: {
			to: {
				type: String,
				required: true
			}
		},
		template: `<a @click="navigate" :href="to">{{ to }}</a>`,
		methods: {
			navigate(evt) {
				evt.preventDefault();
        window.history.pushState(null, null, this.to);
        EventBus.$emit('navigate');
			}
		}
	};
	//
	const routes = [
		{ path: "/", component: A },
		{ path: "/A", component: A },
		{ path: "/B", component: B },
		{ path: "/C", component: C }
	];

	export default {
		name: "App",
		components: {
			"router-view": View,
			"router-link": Link
		}
	};
</script>

<style>
#app {
	font-family: "Avenir", Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
 
  display: flex;
  flex-direction: row;
  justify-content: center

}
.container {
	display: flex;
	flex-direction: column;
	justify-content: center;
  
}
</style>
