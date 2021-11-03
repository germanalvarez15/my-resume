<script lang="ts">
	import { Router, Route, Link } from "svelte-navigator";
	import Intro from "./components/Intro.svelte";
import Stack from "./components/Stack.svelte";
	import Welcome from "./components/Welcome.svelte";
	

</script>
<Router>
	<Route path="/">
		<Welcome/>
	</Route>
	<Route path="/intro">
		<Intro/>
	</Route>
	<Route path="/stack">
		<Stack/>
	</Route>
</Router>
<style>
	:global(body)  {
		width: 100vw;
		height: 100vh;
		overflow: hidden;
		background: #005575;
	}
	:global(.main-container) {
		cursor: pointer;

		position: absolute;
		top: 25vh;
		left: 10vw;
		font: 20px "Arial";
		background-color: #80808054;
		border-radius: 25px;
	}
</style>