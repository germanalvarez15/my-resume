
<script>
    import { useNavigate } from "svelte-navigator";
    import { count } from '../../utils/stores';

    const navigate = useNavigate();
    export let actualPageIndex;
    export let routesMap;
    const routesKeysArray = Object.keys(routesMap);

    const onNextPage = () => {

        actualPageIndex += 1; 
        count.update(n => n=actualPageIndex);

        navigate(routesMap[routesKeysArray[actualPageIndex]]);
    }
  </script>
<div class="right-arrow" on:click="{onNextPage}">
    <img alt="Next" class="arrow" src="assets/arrow.png" />
</div>
<style>

    img{
        width: 100%;
    }
	.right-arrow {
        -webkit-filter: invert(1) opacity(0.5);
		filter: invert(1) opacity(0.5);
        width: 5vw;
	    -webkit-transform: rotate(180deg);
        transform: rotate(180deg);
	}
</style>