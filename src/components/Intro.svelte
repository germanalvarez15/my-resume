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
        let maxDragLeftValue = 250;

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
                } else if (elmnt.offsetLeft >= maxDragLeftValue) {
                    if (elmnt.offsetLeft - pos1 <= elmnt.offsetLeft) {
                        //Only allow to move left
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
            if (elmnt.offsetLeft < minDragLeftValue) {
                visible = false;
                if (moveLeft) {
                    navigate('/stack', { replace: true });
                }else{
                }
            }
            }
        }
    });
</script>
{#if visible}
    <div id="mydiv"  class="main-container" in:fly={{x:10000, duration: 2000}} out:fly={{x:-2000, duration: 2000}}>
        <div class="profile-container">
            <img src="assets/profile-pic.png" />
            <br />
            <div>Nationalities: 🇺🇾 🇮🇹</div>
            <div >Languages: 🇪🇸 🇬🇧 🇮🇹</div>
            <br/>
        </div>
        <div class="description-container">
            <h2 >German Alvarez</h2>
            <p >
            I started with my academic training as a Front-End Programmer at the
            BIOS institute and later, there too, I graduated from the career of
            Videogame Programming.
            <br />
            <br />
            I am currently studying a Bachelor's Degree in Information Technology
            at the Technological University of Uruguay and I am a Front-End
            developer in a professional way.
            <br />
            <br />
            In addition, my experience has led me to be able to dedicate myself as
            a freelance developer of Virtual Reality and Augmented Reality, so I
            also have a strong training in the area.
            </p>
        </div>
    </div>
{/if}
<style>
  img {
  width: 330px;
  margin: 15px;
}

.scroll-wrapper {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: -17px;
  /* Increase/Decrease this value for cross-browser compatibility */
  overflow-y: scroll;
}

.main-container {
cursor: pointer;
  color: white;
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
  -webkit-box-pack: center;
      -ms-flex-pack: center;
          justify-content: center;

}

.description-container {
  width: 50vw;
  margin: 25px;
}

.profile-container {
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

p {
  color: gainsboro;
}

@media only screen and (max-width: 600px) {
  .main-container {
    position: relative;
    top: 0;
    left: 0;
  }
  .description-container {
    width: 90vw;
    margin: auto;
  }
}
/*# sourceMappingURL=intro.css.map */
</style>