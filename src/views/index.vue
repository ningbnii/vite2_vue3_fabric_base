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
  rect.set('fill', 'black')
  rect.set({ strokeWidth: 5, stroke: 'rgba(100,200,200,0.5)' })
  rect.set('angle', 15).set('flipY', true)
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
  var rect2 = new fabric.Rect({ left: 100, top: 100, width: 10, height: 20, fill: '#f55', opacity: 0.7 })
  canvas.add(rect2)
  console.log(rect.get('width'))
})
</script>
<style lang="scss" scoped>
.canvas_box {
  width: 100vw;
  height: 100vh;
}
</style>
