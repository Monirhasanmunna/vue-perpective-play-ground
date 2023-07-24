<script setup>
import { ref, reactive, computed } from 'vue'

const poperties = reactive({
    perspective : 100,
    rotateX     : 0,
    rotateY     : 0,
    rotateZ     : 0
});

const box = computed(()=>{
  return {
    transform : `
      perspective(${poperties.perspective}px)
      rotateX(${poperties.rotateX}deg)
      rotateY(${poperties.rotateY}deg)
      rotateZ(${poperties.rotateZ}deg)
    `
  }
});


const reset = ()=>{
  poperties.perspective = 100,
  poperties.rotateX     = 0,
  poperties.rotateY     = 0,
  poperties.rotateZ     = 0
}


</script>

<template>

  <h2>Perspective Playground</h2>
    <main>
      <section class="settings">
        <div class="settings-container">
          <label>perspective: {{ poperties.perspective }} px;</label>
          <input type="range" min="0" max="999" v-model="poperties.perspective"/>

          <label>rotateX: {{ poperties.rotateX }} deg; </label>
          <input type="range" min="-180" max="180" v-model="poperties.rotateX"/>

          <label>rotateY: {{ poperties.rotateY }} deg; </label>
          <input type="range" min="-180" max="180" v-model="poperties.rotateY"/>

          <label>rotateZ: {{ poperties.rotateZ }} deg; </label>
          <input type="range" min="-180" max="180" v-model="poperties.rotateZ"/>

          <button type="button" @click="reset()">Reset</button>
         
       
        </div>
      </section>
      <section class="output">
        <div class="box-container">
          <div class="box" :style="box"></div>
        </div>
      </section>
    </main>
 
</template>

<style scoped>

</style>