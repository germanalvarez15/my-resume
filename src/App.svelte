<script lang="ts">
	import { Router, Route, Link } from "svelte-navigator";
	import Intro from "./components/Intro.svelte";
	import Stack from "./components/Stack.svelte";
	import Welcome from "./components/Welcome.svelte";
	import BackButton from "./components/utils/BackButton.svelte";
	import FowardButton from "./components/utils/FowardButton.svelte";
	import { count } from "./utils/stores";
	import Experience from "./components/Experience.svelte";
	import Contact from "./components/Contact.svelte";
	import { MetaTags } from 'svelte-meta-tags';

	const routesMap = {
		home: '/',
		intro: '/intro',
		stack: '/stack',
		experience: '/experience',
		contact: '/contact'
	}
	const routesKeysArray = Object.keys(routesMap);
	
	let actualPageIndex;

	count.subscribe(value => {
		actualPageIndex = value;
		
	});

	routesKeysArray.forEach((key,index) => {
		if(routesMap[key] == location.pathname){
			actualPageIndex = index
		}
	})

	let scrollDown = false;
	window.onscroll = (e)=>{
		scrollDown = window.scrollY > 0;
	}
	const onScrollTop = ()=>{
		window.scrollTo(0,0);
	}
</script>

	<MetaTags 
		additionalLinkTags={[
			{
			  rel: 'icon',
			  href: 'https://favicon-generator.org/favicon-generator/htdocs/favicons/2021-11-05/2d27ee9484f4335e01ff06e872dcafb0.ico'
			},
			{
			  rel: 'apple-touch-icon',
			  href: 'https://www.test.ie/touch-icon-ipad.jpg',
			  sizes: '76x76'
			}
		  ]}
	/>
		
<svelte:head>

</svelte:head>
	
<Router>

	<div class="absolute-container">
		{#if actualPageIndex > 1}
			<BackButton actualPageIndex={actualPageIndex} routesMap={routesMap}/>
		{/if}

			<Route path="{routesMap.home}">
				<Welcome/>
			</Route>
			<Route path="{routesMap.intro}">
				<Intro/>
			</Route>
			<Route path="{routesMap.stack}">
				<Stack/>
			</Route>
			<Route path="{routesMap.experience}">
				<Experience/>
			</Route>
			<Route path="{routesMap.contact}">
				<Contact/>
			</Route>

		{#if actualPageIndex < (routesKeysArray.length - 1) && actualPageIndex > 0}
			<FowardButton actualPageIndex={actualPageIndex} routesMap={routesMap}/>
		{/if}
		{#if scrollDown}
			<div class="goTopButton" on:click="{onScrollTop}">
				<img alt="Go top" src="assets/arrow.png">
			</div>
		{/if}
	</div>
</Router>

<style>

	:global(body)  {
		width: 100vw;
		height: 100vh;
		background: #005575;
	}
	
	:global(.absolute-container) {
		display: -webkit-box;
		display: -ms-flexbox;
		display: flex;
		-webkit-box-orient: horizontal;
		-webkit-box-direction: normal;
      	-ms-flex-direction: row;
		flex-direction: row;
  		-ms-flex-wrap: wrap;
      	flex-wrap: wrap;
		-webkit-box-align: center;
		-ms-flex-align: center;
		align-items: center;
		justify-content: center;
		margin-top: 8%;
	}
	:global(.main-container) {
		font: 20px "Arial";
		background-color: #80808054;
		border-radius: 25px;
	}
	:global(.arrow) {
  		-webkit-filter: invert(1) opacity(0.5);
          filter: invert(1) opacity(0.5);
		width: 100%;
	}

	:global(.left-arrow),
	:global(.right-arrow) {
		width: 5vw;
	}

	:global(.right-arrow) {
		-webkit-transform: rotate(180deg);
		transform: rotate(180deg);
	}

	@media only screen and (max-width: 650px) {

		:global(.absolute-container) {
			-webkit-box-pack: center;
        	-ms-flex-pack: center;
            justify-content: center;
    		margin-top: 0;
		}

		:global(.left-arrow),
		:global(.right-arrow) {
			width: 25vw;
		}
		:global(.left-arrow) {
			-webkit-box-ordinal-group: 2;
			-ms-flex-order: 1;
			order: 1;
		}
		:global(.right-arrow) {
			-webkit-box-ordinal-group: 3;
			-ms-flex-order: 2;
			order: 2;
		}
		:global(.main-container){
			-webkit-box-ordinal-group: 4;
			-ms-flex-order: 3;
			order: 3;
		}
		:global(.model-container) {
			width: 80vw !important;
		}
		.goTopButton{
			width: 10vw;
			height: 5vh;
			position: fixed;
			left: 10vw;
			bottom: 10vh;
			background-color: #005575;
			border-radius: 25px;
    		border: solid 1px white;
		}
		.goTopButton > img{
			-webkit-filter: invert(1) opacity(0.5);
          	filter: invert(1) opacity(0.5);
			transform: rotate(90deg);
			width:100%;
			height: 100%;
		}
	}	
</style>