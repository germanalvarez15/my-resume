<script lang="ts">
    import { useNavigate, useLocation } from "svelte-navigator";
    const navigate = useNavigate();
    const location = useLocation();

    const onClick = () =>{
        navigate('/intro', { replace: true });
    }
</script>

<div class="main-container-welcome">
    <div id="letter-object" class="text-pop-up-top">Welcome!</div>
    <button on:click="{onClick}" class="intro-button scale-up-center">About me</button>
</div>

<style>


.main-container-welcome {
    height: 100%;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    justify-content: space-evenly;

    align-items: center;
}

.intro-button {
  cursor: pointer;
  color: white;
  font-size: larger;
  font-weight: 700;
  border-radius: 10px;
  background-color: #06d706;
  width: 25vw;
  height: 7vh;
  border-top-style: none;
  border-right-style: none;
  border-left-style: none;
  border-bottom: 5px #00000026 solid;
}

.intro-button:hover {
  -webkit-animation: scale-down-center 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
  animation: scale-down-center 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
}

#letter-object {
  color: #fff;
  font: 20vw "Arial";
  text-transform: none;
  text-align: center;
  margin: 0 15px 0 15px;
}

.scale-up-center {
  -webkit-animation: scale-up-center 0.4s cubic-bezier(0.39, 0.575, 0.565, 1) both;
  animation: scale-up-center 0.4s cubic-bezier(0.39, 0.575, 0.565, 1) both;
}

.scale-down-center {
  -webkit-animation: scale-down-center 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
  animation: scale-down-center 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
}

.text-pop-up-top {
  -webkit-animation: text-pop-up-top 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
  animation: text-pop-up-top 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
}

@-webkit-keyframes scale-up-center {
  0% {
    -webkit-transform: scale(0.8);
    transform: scale(0.8);
  }
  100% {
    -webkit-transform: scale(1);
    transform: scale(1);
  }
}

@keyframes scale-up-center {
  0% {
    -webkit-transform: scale(0.8);
    transform: scale(0.8);
  }
  100% {
    -webkit-transform: scale(1);
    transform: scale(1);
  }
}

@-webkit-keyframes scale-down-center {
  0% {
    -webkit-transform: scale(1);
    transform: scale(1);
  }
  100% {
    -webkit-transform: scale(0.8);
    transform: scale(0.8);
  }
}

@keyframes scale-down-center {
  0% {
    -webkit-transform: scale(1);
    transform: scale(1);
  }
  100% {
    -webkit-transform: scale(0.8);
    transform: scale(0.8);
  }
}

@-webkit-keyframes text-pop-up-top {
  0% {
    -webkit-transform: translateY(0);
    transform: translateY(0);
    -webkit-transform-origin: 50% 50%;
    transform-origin: 50% 50%;
    text-shadow: none;
  }
  100% {
    -webkit-transform: translateY(-50px);
    transform: translateY(-50px);
    -webkit-transform-origin: 50% 50%;
    transform-origin: 50% 50%;
    text-shadow: 0 1px 0 #cccccc, 0 2px 0 #cccccc, 0 3px 0 #cccccc, 0 4px 0 #cccccc, 0 5px 0 #cccccc, 0 6px 0 #cccccc, 0 7px 0 #cccccc, 0 8px 0 #cccccc, 0 9px 0 #cccccc, 0 50px 30px rgba(0, 0, 0, 0.3);
  }
}

@keyframes text-pop-up-top {
  0% {
    -webkit-transform: translateY(0);
    transform: translateY(0);
    -webkit-transform-origin: 50% 50%;
    transform-origin: 50% 50%;
    text-shadow: none;
  }
  100% {
    -webkit-transform: translateY(-50px);
    transform: translateY(-50px);
    -webkit-transform-origin: 50% 50%;
    transform-origin: 50% 50%;
    text-shadow: 0 1px 0 #cccccc, 0 2px 0 #cccccc, 0 3px 0 #cccccc, 0 4px 0 #cccccc, 0 5px 0 #cccccc, 0 6px 0 #cccccc, 0 7px 0 #cccccc, 0 8px 0 #cccccc, 0 9px 0 #cccccc, 0 50px 30px rgba(0, 0, 0, 0.3);
  }
}

@media only screen and (max-width: 600px) {
  .intro-button {
    width: 60vw;
    height: 10vh;
    font-size: 30px;
  }
}

</style>