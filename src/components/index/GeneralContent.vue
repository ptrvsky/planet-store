<template>
  <div class="general-content">
    <div class="content">
      <div class="side left">
        <div class="planet-model-container">
          <div class="model" ref="planetModelContainer"><!-- THREE.JS EARTH MODEL --></div>
          <div class="background-light"></div>
        </div>
      </div>
      <div class="side right">
        <span class="top-text">Customizable planets for your business</span>
        <span class="bottom-text">
          Hundreds of satisfied customers used our planets to take their businesses to the next level.
        </span>
        <div class="button">Browse planets</div>
      </div>
    </div>
  </div>
</template>

<script>
import * as THREE from 'three';
import {GLTFLoader} from 'three/examples/jsm/loaders/GLTFLoader.js';

export default {
  name: "GeneralContent",
  methods: {
    addPlanetModel() {
      const modelContainer = this.$refs.planetModelContainer;
      if (!modelContainer) return;

      const scene = new THREE.Scene();
      const camera = new THREE.PerspectiveCamera(
          85,
          modelContainer.offsetWidth / modelContainer.offsetHeight,
          0.1,
          1000);
      const renderer = new THREE.WebGLRenderer({
        alpha: true,
        antialias: true
      });
      renderer.setSize(modelContainer.offsetWidth, modelContainer.offsetHeight);
      modelContainer.appendChild(renderer.domElement);

      const light = new THREE.HemisphereLight(0xffffbb, 0x080820, 1);
      scene.add(light);

      const loader = new GLTFLoader();
      let earth;
      loader.load('./assets/earth.gltf', function (gltf) {
        earth = gltf.scene;
        scene.add(earth);
      }, undefined, function (error) {
        console.error(error);
      });

      camera.position.z = 2;

      function animate() {
        requestAnimationFrame(animate);
        if (earth) earth.rotation.y += 0.002;
        renderer.render(scene, camera);
      }

      animate();
    }
  },
  mounted() {
    this.addPlanetModel();
  }
}


</script>

<style scoped lang="scss">
.general-content {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  z-index: 2;

  .content {
    max-width: 1280px;
    width: 1280px;
    min-height: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 0 20px;

    @media only screen and (max-width: 1100px) {
      flex-direction: column;
      justify-content: flex-start;
    }

    .side {
      &.left {
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 100%;

        @media only screen and (max-width: 1100px) {
          min-height: unset;
          margin-top: 100px;
        }

        .planet-model-container {
          position: relative;
          width: 500px;
          height: 500px;
          z-index: 10;

          @media only screen and (max-width: 1100px) {
            width: 250px;
            height: 250px;
          }

          .model, .background-light {
            position: absolute;
            width: 100%;
            height: 100%;
          }

          .model {
            z-index: 5;
          }

          .background-light {
            background-color: gray;
            border-radius: 50%;
            filter: blur(70px);
            opacity: 0.2;
          }
        }
      }

      &.right {
        display: flex;
        flex-direction: column;
        align-items: flex-end;
        max-width: 500px;
        text-align: right;

        @media only screen and (max-width: 1100px) {
          align-items: center;
          text-align: center;
          margin-top: 10px;

          font-size: 0.8em;
        }

        .top-text {
          font-size: 2.7em;
          font-weight: 700;
          text-shadow: 0 0 5px black
        }

        .bottom-text {
          margin-top: 25px;
          max-width: 450px;
          text-shadow: 0 0 5px black
        }

        .button {
          border-radius: 10px;
          background: linear-gradient(180deg, rgba(250, 0, 255, 1) 0%, rgba(255, 0, 77, 1) 100%);
          padding: 20px 60px;
          font-weight: 500;
          margin-top: 35px;
          box-shadow: 0 4px 10px 0 black;
          z-index: 5;

          &:hover {
            cursor: pointer;
          }
        }
      }
    }
  }
}
</style>