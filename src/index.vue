<template>
  <main>
    <div class="dropzone">
      <div id="draggable" draggable="true" 
        @dragstart="dragstart($event)">
        This div is draggable
      </div>
    </div>
    <div class="dropzone" @dragover="dragover($event)" @dragleave="dragleave($event)" @dragenter="dragenter($event)"></div>
    <div class="dropzone" @dragover="dragover($event)" @dragleave="dragleave($event)" @dragenter="dragenter($event)"></div>
    <div class="dropzone" @dragover="dragover($event)" @dragleave="dragleave($event)" @dragenter="dragenter($event)"></div>
  </main>
</template>

<script>
export default {
  name: 'App',
  methods: {
    dragstart (event, content) {
      console.log(event, content)
      event.dataTransfer.setData('text/plain',null)
      this.target = event.target
    },
    dragend (event, content) {
      // console.log(event, content)
      // firefox not emit clientX and Y by drag
    },
    dragover (event, content) {
      // console.log(event, content)
      // event.target.style.background = "red";
    },
    dragenter (event, content) {
      console.log(event, content)
      event.target.style.background = "blue";
    },
    dragleave (event, content) {
      console.log(event, content)
      event.target.style.background = "blueviolet";
    },
    drag (event, content) {
      // console.log(event, content)
      // firefox not emit clientX and Y by drag
    }
  }
}
</script>

<style scoped>
#draggable {
  width: 200px;
  height: 20px;
  text-align: center;
  background: white;
}

.dropzone {
  width: 200px;
  height: 20px;
  background: blueviolet;
  margin-bottom: 10px;
  padding: 10px;
}
</style>
