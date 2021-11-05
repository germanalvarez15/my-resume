
<script>
    import { fade } from 'svelte/transition';

</script>
<div class="main-container" in:fade={{ delay: 250, duration: 500 }}>
    <div class="profile-container" >
        <img alt='German Alvarez' src="assets/profile-pic.png" />
        <br />
        <div>Nationalities: 🇺🇾 🇮🇹</div>
        <div >Languages: 🇪🇸 🇬🇧 🇮🇹</div>
        <br/>
    </div>
    <div class="description-container" >
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
    <div class="model-container" >
        <model-viewer 
            src="assets/models/Godzilla.glb" 
            ar 
            ar-modes="webxr scene-viewer quick-look" 
            seamless-poster 
            shadow-intensity="1"
            camera-controls
        ></model-viewer>
        <p style="font-size: small; text-align: center; color: black">
            3D model by:
            <a href="https://artsandculture.google.com/project/ar">Google</a>
        </p>
    </div>
</div>
<style>
  h2{
    text-align: center;
  }
  img {
    width: 100%;
    margin: 3%;
  }

  .main-container {
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
    width: 35vw;
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
    width: 20vw;
  }

  p {
    color: gainsboro;
  }

  .model-container {
    width: 30vw;
    height: 60vh;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-orient: vertical;
    -webkit-box-direction: normal;
        -ms-flex-direction: column;
            flex-direction: column;
    -ms-flex-wrap: nowrap;
        flex-wrap: nowrap;
    -webkit-box-align: center;
        -ms-flex-align: center;
            align-items: center;
  }

  model-viewer {
    height: 100%;
    width: 100%;
  }


  @-webkit-keyframes slide-out-left {
    0% {
      -webkit-transform: translateX(0);
      transform: translateX(0);
      opacity: 1;
    }
    100% {
      -webkit-transform: translateX(-1000px);
      transform: translateX(-1000px);
      opacity: 0;
    }
  }

  @keyframes slide-out-left {
    0% {
      -webkit-transform: translateX(0);
      transform: translateX(0);
      opacity: 1;
    }
    100% {
      -webkit-transform: translateX(-1000px);
      transform: translateX(-1000px);
      opacity: 0;
    }
  }

  @media only screen and (max-width: 650px) {
    .description-container {
      width: 90vw;
      margin: auto;
    }
    .main-container {
      position: relative;
      top: 0;
      left: 0;

    }
    .profile-container {
      width: 65vw;
    }

  }
/*# sourceMappingURL=intro.css.map */
</style>