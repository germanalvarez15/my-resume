<script>
    import { useNavigate } from "svelte-navigator";
    import { count } from '../../utils/stores';
	import { checkKey, keyPressed } from "../../utils/keyevent";

    const navigate = useNavigate();
    export let actualPageIndex;
    export let routesMap;
    const routesKeysArray = Object.keys(routesMap);

    document.addEventListener("keydown",
		() =>{
			checkKey();
            if(keyPressed == 'left'){
                onPreviousPage();
            }
		}
	)
    const onPreviousPage = () => {

        actualPageIndex -= 1; 
        count.update(n => n =actualPageIndex);

        navigate(routesMap[routesKeysArray[actualPageIndex]]);
    }
  </script>
<div class="left-arrow" on:click="{onPreviousPage}">
    <img alt="Previous" class="arrow" src="assets/arrow.png" />
</div>  
<style>
        img{
        width: 100%;
    }
</style>