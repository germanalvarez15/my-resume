<script>
    import { onMount } from 'svelte';
    import { fly } from 'svelte/transition';
    import { useNavigate, useLocation } from "svelte-navigator";

    let visible = true;
    const navigate = useNavigate();
    const location = useLocation();

    onMount(() => {    
        // Make the DIV element draggable:
        dragElement(document.getElementById("mydiv"));
        let moveLeft = false;
        let minDragLeftValue = 50;
        let maxDragLeftValue = 550;

        function dragElement(elmnt) {
            var pos1 = 0,
            pos2 = 0,
            pos3 = 0,
            pos4 = 0;
            if (document.getElementById(elmnt.id + "header")) {
                // if present, the header is where you move the DIV from:
                document.getElementById(elmnt.id + "header").onmousedown =
                    dragMouseDown;
            } else {
                // otherwise, move the DIV from anywhere inside the DIV:
                elmnt.onmousedown = dragMouseDown;
            }

            function dragMouseDown(e) {
                e = e || window.event;
                e.preventDefault();
                // get the mouse cursor position at startup:
                pos3 = e.clientX;
                pos4 = e.clientY;
                document.onmouseup = closeDragElement;
                // call a function whenever the cursor moves:
                document.onmousemove = elementDrag;
            }

            function elementDrag(e) {
                e = e || window.event;
                e.preventDefault();
                // calculate the new cursor position:
                pos1 = pos3 - e.clientX;
                pos2 = pos4 - e.clientY;
                pos3 = e.clientX;
                pos4 = e.clientY;

                //Move left more than minDragLeftValue and move right less than maxDragLeftValue
                if (
                    elmnt.offsetLeft > minDragLeftValue &&
                    elmnt.offsetLeft < maxDragLeftValue
                ) {
                    if (elmnt.offsetLeft - pos1 > elmnt.offsetLeft) {
                        console.log("RIGHT");
                        moveLeft = false;
                    } else {
                        console.log("LEFT");
                        moveLeft = true;
                    }
                    elmnt.style.left = elmnt.offsetLeft - pos1 + "px";
                } else if (elmnt.offsetLeft >= maxDragLeftValue) { //If is in the limit of the right
                    console.log('On the limit!!');
                    //Only allow to move left
                    if (elmnt.offsetLeft - pos1 <= elmnt.offsetLeft) {
                        elmnt.style.left = elmnt.offsetLeft - pos1 + "px";
                    }
                }

                // set the element's new position:
                //elmnt.style.top = elmnt.offsetTop - pos2 + "px";  
            }

            function closeDragElement() {
            // stop moving when mouse button is released:
            document.onmouseup = null;
            document.onmousemove = null;
            visible = false;

                if (
                    elmnt.offsetLeft <= minDragLeftValue //if its on the left limit
                ) {
                }
                else if(
                    elmnt.offsetLeft >= maxDragLeftValue //Or on the right limit
                ){
                    navigate('/intro', { replace: true });
                }
            }
        }
    });
</script>
{#if visible}
<div id="mydiv" class="main-container " in:fly={{x:10000, duration: 2000}} out:fly={{x:-2000, duration: 2000}}>
    <h2>My skills</h2>
    <div class="column-container">
      <div class="column-1">
        <div class="skill">
          <img src="/assets/stacks/angular.png" />
          <div class="rate">
            <label for="star5" title="text">5 stars</label>
            <label for="star4" title="text" class="fill">4 stars</label>
            <label for="star3" title="text" class="fill">3 stars</label>
            <label for="star2" title="text" class="fill">2 stars</label>
            <label for="star1" title="text" class="fill">1 star</label>
          </div>
        </div>
        <div class="skill">
          <img
            src="https://sujanbyanjankar.com.np/wp-content/uploads/2019/01/React.js_logo-512.png"
          />
          <div class="rate">
            <label for="star5" title="text">5 stars</label>
            <label for="star4" title="text">4 stars</label>
            <label for="star3" title="text">3 stars</label>
            <label for="star2" title="text" class="fill">2 stars</label>
            <label for="star1" title="text" class="fill">1 star</label>
          </div>
        </div>
        <div class="skill">
          <img
            src="https://raw.githubusercontent.com/sveltejs/svelte/29052aba7d0b78316d3a52aef1d7ddd54fe6ca84/site/static/images/svelte-android-chrome-512.png"
          />
          <div class="rate">
            <label for="star5" title="text">5 stars</label>
            <label for="star4" title="text" class="">4 stars</label>
            <label for="star3" title="text" class="">3 stars</label>
            <label for="star2" title="text" class="fill">2 stars</label>
            <label for="star1" title="text" class="fill">1 star</label>
          </div>
        </div>
        <div class="skill">
          <img src="/assets/stacks/sass.png" />
          <div class="rate">
            <label for="star5" title="text">5 stars</label>
            <label for="star4" title="text" class="fill">4 stars</label>
            <label for="star3" title="text" class="fill">3 stars</label>
            <label for="star2" title="text" class="fill">2 stars</label>
            <label for="star1" title="text" class="fill">1 star</label>
          </div>
        </div>
        <div class="skill">
          <img
            src="https://www.kojac.nl/tailwind/images/Backend/nodejs.png"
          />
          <div class="rate">
            <label for="star5" title="text">5 stars</label>
            <label for="star4" title="text" class="">4 stars</label>
            <label for="star3" title="text" class="">3 stars</label>
            <label for="star2" title="text" class="">2 stars</label>
            <label for="star1" title="text" class="fill">1 star</label>
          </div>
        </div>
      </div>
      <div class="column-2">
        <div class="skill">
          <img
            src="https://cdn4.iconfinder.com/data/icons/logos-brands-5/24/unity-512.png"
          />
          <div class="rate">
            <label for="star5" title="text">5 stars</label>
            <label for="star4" title="text" class="">4 stars</label>
            <label for="star3" title="text" class="fill">3 stars</label>
            <label for="star2" title="text" class="fill">2 stars</label>
            <label for="star1" title="text" class="fill">1 star</label>
          </div>
        </div>
        <div class="skill">
          <img
            src="https://www.avrspot.com/wp-content/uploads/2018/06/vuforia-logo.png"
          />
          <div class="rate">
            <label for="star5" title="text">5 stars</label>
            <label for="star4" title="text" class="fill">4 stars</label>
            <label for="star3" title="text" class="fill">3 stars</label>
            <label for="star2" title="text" class="fill">2 stars</label>
            <label for="star1" title="text" class="fill">1 star</label>
          </div>
        </div>
        <div class="skill">
          <img
            src="https://miro.medium.com/max/256/1*hJdmqVuL79jo8ly7_TvI0Q.png"
          />
          <div class="rate">
            <label for="star5" title="text">5 stars</label>
            <label for="star4" title="text" class="">4 stars</label>
            <label for="star3" title="text" class="fill">3 stars</label>
            <label for="star2" title="text" class="fill">2 stars</label>
            <label for="star1" title="text" class="fill">1 star</label>
          </div>
        </div>
        <div class="skill">
          <img
            src="https://zenprospect-production.s3.amazonaws.com/uploads/pictures/605caf6df029e30001baf768/picture"
          />
          <div class="rate">
            <label for="star5" title="text">5 stars</label>
            <label for="star4" title="text" class="">4 stars</label>
            <label for="star3" title="text" class="fill">3 stars</label>
            <label for="star2" title="text" class="fill">2 stars</label>
            <label for="star1" title="text" class="fill">1 star</label>
          </div>
        </div>
        <div class="skill">
          <img
            src="https://upload.wikimedia.org/wikipedia/commons/9/92/A-Frame_logo.png"
          />
          <div class="rate">
            <label for="star5" title="text">5 stars</label>
            <label for="star4" title="text" class="">4 stars</label>
            <label for="star3" title="text" class="fill">3 stars</label>
            <label for="star2" title="text" class="fill">2 stars</label>
            <label for="star1" title="text" class="fill">1 star</label>
          </div>
        </div>
      </div>
      <div class="column-3">
        <div class="skill">
          <img src="/assets/stacks/firebase.png" />
          <div class="rate">
            <label for="star5" title="text">5 stars</label>
            <label for="star4" title="text" class="">4 stars</label>
            <label for="star3" title="text" class="">3 stars</label>
            <label for="star2" title="text" class="fill">2 stars</label>
            <label for="star1" title="text" class="fill">1 star</label>
          </div>
        </div>
        <div class="skill">
          <img src="https://cdn.icon-icons.com/icons2/2107/PNG/512/file_type_flutter_icon_130599.png"/>
          <div class="rate">
            <label for="star5" title="text">5 stars</label>
            <label for="star4" title="text" class="">4 stars</label>
            <label for="star3" title="text" class="">3 stars</label>
            <label for="star2" title="text" class="">2 stars</label>
            <label for="star1" title="text" class="fill">1 star</label>
          </div>
        </div>
      </div>
    </div>
  </div>
{/if}
<style>
    @charset "UTF-8";
    .main-container {
    color: white;
    top: 15vh;
    left: 25vw;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-orient: vertical;
    -webkit-box-direction: normal;
        -ms-flex-direction: column;
            flex-direction: column;
    -ms-flex-wrap: wrap;
        flex-wrap: wrap;
    -webkit-box-align: center;
        -ms-flex-align: center;
            align-items: center;
    }

    .column-container {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-orient: horizontal;
    -webkit-box-direction: normal;
        -ms-flex-direction: row;
            flex-direction: row;
    -ms-flex-wrap: wrap;
        flex-wrap: wrap;
    -ms-flex-pack: distribute;
        justify-content: space-around;
    }

    img {
    width: 5vw;
    }

    .skill {
    margin: 15px;
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
    }

    .rate {
    padding-left: 10px;
    }

    .rate > label {
    float: right;
    width: 1em;
    overflow: hidden;
    white-space: nowrap;
    cursor: pointer;
    font-size: 30px;
    color: #ccc;
    }

    .rate:not(:checked) > label:before {
    content: "★ ";
    }

    .fill:before {
    color: #ffc700;
    }

    @media only screen and (max-width: 650px) {
    body {
        overflow: scroll;
    }
    .main-container {
        top: 2vh;
        left: 0;
        margin: 2%;
    }
    img {
        width: 20vw;
    }
    }

    @media only screen and (min-width: 650px) and (max-width: 850px) {
    .main-container {
        top: 8vh;
        left: 5vw;
    }
    }

    @media only screen and (min-width: 850px) and (max-width: 1000px) {
    .main-container {
        left: 10vw;
    }
    }

    @media only screen and (min-width: 1000px) and (max-width: 1200px) {
    .main-container {
        left: 20vw;
    }
    }
    /*# sourceMappingURL=stack.css.map */
</style>