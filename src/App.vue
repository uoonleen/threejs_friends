<template>
  <div id="app">

  </div>
</template>

<script>
import * as Three from 'three';

export default {
  name: 'app',
  data () {
    return {
      camera: '',
      scene: '',
      renderer: ''
    }
  },
  created() {
    this.scene = new Three.Scene();
    this.camera = new Three.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
    this.renderer = new Three.WebGLRenderer();
    this.renderer.setSize(window.innerWidth, window.innerHeight);

    let app = document.getElementById('app');
    app.appendChild(this.renderer.domElement);

    this.gameLoop(); 
  },
  methods: {
    // game logic
    update() {

    },

    // draw scene
    render() {
      this.renderer.render(this.scene, this.camera);      
    },

    // run game loop (update, render, repeat)
    gameLoop() {
      requestAnimationFrame(this.gameLoop);

      this.update();
      this.render();
    }
  }
}
</script>

<style lang="scss">
html, body, #app {
  background: dimgrey;
  color: sienna;
  margin: 0;
}

canvas {
  width: 100%;
  height: 100%;
}
</style>
