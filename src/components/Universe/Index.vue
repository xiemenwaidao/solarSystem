<template>
  <div id="canvas_wrap">
    <ul>
      <li v-for="p in pArray" :key="p"  @click="changePlanet(p)" :class="pName===p ? 'red' : ''">
        {{p}}
      </li>
      <li id="distance"></li>
    </ul>
    <canvas id="webgl_canvas" ref="canvas" />
    <p id="license_txt">Low Poly Spaceship by <a href="https://market.pmnd.rs/creator/edwinrc" target="_blank" rel="noopener">EdwinRC</a>,&nbsp;<a href="https://creativecommons.org/licenses/by/2.0/" target="_blank" rel="noopener">CC-BY</a></p>
  </div>
</template>
<script>
import MyGL from "./js/MyGL"
export default {
  data() {
    return {
      pArray:['mercury','venus','earth','mars','jupiter','saturn','uranus','neptune'],
      pName: 'earth'
    }
  },
  mounted() {
    if(!this.MyGL) {
      this.MyGL = new MyGL({
        $canvas: this.$refs.canvas
      })
    }
  },
  methods: {
    changePlanet(name) {
      this.pName = name
      this.MyGL.changePlanet(name)
    }
  }
}
</script>
<style scoped>
#canvas_wrap {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
#webgl_canvas {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  margin: auto;
}
ul {
  position: absolute;
  top: 10vh;
  color: #fff;
  cursor: pointer;
  z-index: 2;
}
ul li:hover {
  color: #9797f7;
}
.red {
  color: red !important;
}
#distance {
  color: #9205d4;
}
#license_txt {
  position: absolute;
  bottom: 0;
  right: 10px;
  color: #fff;
  font-size: .5rem;
}
#license_txt > a {
  color: #ff0;
}
</style>
