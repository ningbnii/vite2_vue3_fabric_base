<template>
  <div class="canvas_box" ref="canvasBox">
    <canvas ref="myCanvas"></canvas>
  </div>
</template>
<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

let myCanvas = ref(null)
let canvasBox = ref(null)
onMounted(() => {
  var canvas = new fabric.Canvas(myCanvas.value, {
    width: canvasBox.value.clientWidth,
    height: canvasBox.value.clientHeight,
    backgroundColor: '#ccc',
  })
  var rect = new fabric.Rect({
    left: 100,
    top: 100,
    fill: 'red',
    width: 200,
    height: 200,
    angle: 45,
  })

  canvas.add(rect)
  rect.set({
    left: canvasBox.value.clientWidth / 2,
    top: canvasBox.value.clientHeight / 2,
  })
  var circle = new fabric.Circle({
    radius: 20,
    fill: 'green',
    left: 100,
    top: 100,
  })
  var triangle = new fabric.Triangle({
    width: 20,
    height: 30,
    fill: 'blue',
    left: 50,
    top: 50,
  })
  canvas.add(circle, triangle)
})
</script>
<style lang="scss" scoped>
.canvas_box {
  width: 100vw;
  height: 100vh;
}
</style>
