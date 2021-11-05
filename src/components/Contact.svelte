<script>
    import { fade } from 'svelte/transition';

</script>
<div class="main-container" in:fade={{ delay: 250, duration: 500}}>
    <h2>Contact me</h2>
    <div class="column-container">
      <div class="column">
        <a
          href="https://www.linkedin.com/in/german-alvarez/"
          target="_blank"
        >
          <img
            alt="Linkedin"
            src="https://cdn-icons-png.flaticon.com/512/174/174857.png"
          />
        </a>
      </div>
      <div class="column">
        <a href="https://github.com/germanalvarez15" target="_blank">
          <img
            alt="Github"
            src="https://cdn.iconscout.com/icon/free/png-256/github-154-675675.png"
          />
        </a>
      </div>
      <div class="column">
        <a href="mailto:germanalvarez15@live.com">
          <img
            alt="email"
            src="https://techcommunity.microsoft.com/t5/image/serverpage/image-id/172206i70472167E79B9D0F?v=v2"
          />
        </a>
      </div>
      <div class="model-container">
        <model-viewer
          src="/assets/models/ModuloApollo11.glb"
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
  -webkit-box-align: center;
      -ms-flex-align: center;
          align-items: center;
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

.column > a {
  width: 60%;
}

.column > a > img {
  width: 100%;
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

@media only screen and (max-width: 650px) {
  .column-container {
    -webkit-box-orient: vertical;
    -webkit-box-direction: normal;
        -ms-flex-direction: column;
            flex-direction: column;
    width: 90vw;
  }
  .column {
    width: 100%;
  }
}
/*# sourceMappingURL=contact.css.map */
  </style>