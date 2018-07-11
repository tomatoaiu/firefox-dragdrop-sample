<template>
  <main>
    <div class="left">
      <div class="dropzone">
        <div id="draggable" draggable="true" 
          @dragstart="dragstart($event)">
          This div is draggable
        </div>
      </div>
      <div class="dropzone dropzone-big" @dragover="dragover($event)" @dragleave="dragleave($event)" @dragenter="dragenter($event)">
        <div class="dropzone" @dragover="dragover($event)" @dragleave="dragleave($event)" @dragenter="dragenter($event)"></div>
        <div class="dropzone" @dragover="dragover($event)" @dragleave="dragleave($event)" @dragenter="dragenter($event)"></div>
        <div class="dropzone" @dragover="dragover($event)" @dragleave="dragleave($event)" @dragenter="dragenter($event)"></div>
        <div class="dropzone" @dragover="dragover($event)" @dragleave="dragleave($event)" @dragenter="dragenter($event)"></div>
        <div class="dropzone  dropzone-big" @dragover="dragover($event)" @dragleave="dragleave($event)" @dragenter="dragenter($event)">
          <div class="dropzone" @dragover="dragover($event)" @dragleave="dragleave($event)" @dragenter="dragenter($event)"></div>
          <div class="dropzone" @dragover="dragover($event)" @dragleave="dragleave($event)" @dragenter="dragenter($event)"></div>
          <div class="dropzone  dropzone-big" @dragover="dragover($event)" @dragleave="dragleave($event)" @dragenter="dragenter($event)">
            <div class="dropzone" @dragover="dragover($event)" @dragleave="dragleave($event)" @dragenter="dragenter($event)"></div>
            <div class="dropzone" @dragover="dragover($event)" @dragleave="dragleave($event)" @dragenter="dragenter($event)"></div>
            <div class="dropzone text" @dragover="dragover($event)" @dragleave="dragleave($event)" @dragenter="dragenter($event)">
              一番上のdomのdragoberが働く
              firefixではここに書いてある文字の上にカーソルがくると、dragoverの状態にならない
            </div>
          </div>
        </div>
      </div>
    </div>
   <div class="left">
      <div class="dropzone" @mouseover="mouseover($event)" @mouseleave="mouseleave($event)"></div>
      <div class="dropzone  dropzone-big" @mouseover="mouseover($event)" @mouseleave="mouseleave($event)">
        <div class="dropzone" @mouseover="mouseover($event)" @mouseleave="mouseleave($event)"></div>
        <div class="dropzone" @mouseover="mouseover($event)" @mouseleave="mouseleave($event)"></div>
        <div class="dropzone text yoko" @mouseover="mouseover($event)" @mouseleave="mouseleave($event)">
          firefixではここに書いてある文字の上にカーソルがきてもover状態になる
        </div>
        <div class="dropzone text yoko" @mouseover.prevent="mouseover($event)" @mouseleave.prevent="mouseleave($event)">
          firefixではここに書いてある文字の上にカーソルがきてもover状態になる
        </div>
      </div>
   </div>
  </main>
</template>

<script>
export default {
  name: "App",
  methods: {
    mouseover (event, content) {
      event.target.style.background = "blue";
      
    },
     mouseleave (event, content) {
      event.target.style.background = "blueviolet";
    },
    dragstart(event, content) {
      console.log(event, content);
      event.dataTransfer.setData("text/plain", null);
      this.target = event.target;
    },
    dragend(event, content) {
      // console.log(event, content)
      // firefox not emit clientX and Y by drag
    },
    dragover(event, content) {
      // console.log(event, content)
      // event.target.style.background = "red";
    },
    dragenter(event, content) {
      console.log(event, content);
      event.target.style.background = "blue";
    },
    dragleave(event, content) {
      console.log(event, content);
      event.target.style.background = "blueviolet";
    },
    drag(event, content) {
      // console.log(event, content)
      // firefox not emit clientX and Y by drag
    }
  }
};
</script>

<style scoped>
.left {
  float: left;
  padding-right: 3rem;
}

.right {
  float: right;
}

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
  border: 1px solid #111;
}

.dropzone-big {
  width: 300px;
  height: 300px;
}

.text {
  width: 200px;
  height: 100px;
}

.yoko {
  width: 400px;
}
</style>
