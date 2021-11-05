<script>
    import { fade } from 'svelte/transition';

</script>
<div  class="main-container" in:fade={{ delay: 250, duration: 500}}>
    <h2 >My experience</h2>
    <div class="column-container" >
      <div class="column">
        <img alt="Middlesoft" src="assets/experience/middlesoft.jfif" />
        <b>AR & VR Developer</b>
        <div style="color: gray">(July 2018 - June 2019)</div>
        <div style="color: rgb(24, 24, 24); text-align: center; width: 75%">
          AR & VR Development using Unity as engine.
        </div>
      </div>
      <div class="column">
        <img alt="Solcre" src="assets/experience/solcre.png" />
        <b>Front-End Developer</b>
        <div style="color: gray">(June 2019 - January 2021)</div>
        <div style="color: rgb(24, 24, 24); text-align: center; width: 75%">
          Front End Development using technologies such as Angular2, RxJs,
          Javascript, Firebase, Cordova, SASS and others..
        </div>
      </div>
      <div class="column">
        <img alt="Altimetrik" src="assets/experience/altimetrik.png" />
        <b>AR & VR Developer</b>
        <div style="color: gray">(July 2018 - June 2019)</div>
        <div style="color: rgb(24, 24, 24); text-align: center; width: 65%">
          AR & VR Development using Unity as engine.
        </div>
      </div>
      <div class="model-container">
        <model-viewer
          src="assets/models/PacMan.glb"
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
  </div>
  <style>
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

.column {
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
  -ms-flex-line-pack: center;
      align-content: center;
  width: 20vw;
}

.column > * {
  margin-top: 5%;
}
.column > img {
  width: 60%;
}
.model-container {
  width: 25vw;
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

@media only screen and (max-width: 650px) {
  .column-container {
    flex-direction: column;
    align-items: center;
    width: 90vw;
  }
  .column {
    width: 100%;
  }
}
@media only screen and (min-width: 650px) and (max-width: 850px) {
}
@media only screen and (min-width: 850px) and (max-width: 1000px) {
}
@media only screen and (min-width: 1000px) and (max-width: 1200px) {
}
/*# sourceMappingURL=experience.css.map */
  </style>