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
      renderer: '',
      cube: ''
    }
  },
  created() {
    this.scene = new Three.Scene();
    this.camera = new Three.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
    this.renderer = new Three.WebGLRenderer();
    this.renderer.setSize(window.innerWidth, window.innerHeight);

    document.body.appendChild(this.renderer.domElement);

    // create the shape
    let geometry = new Three.BoxGeometry(1, 1, 1);

    // create a material, color or image texture
    let material = new Three.MeshBasicMaterial({ color: 0xFFFFFF, wireframe: false });
    this.cube = new Three.Mesh(geometry, material);
    
    this.scene.add(this.cube);



    this.camera.position.z = 3;

    this.gameLoop(); 
  },
  methods: {
    // game logic
    update() {
      this.cube.rotation.x += 0.01;
      this.cube.rotation.y += 0.005;
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
