<script setup>

import { onMounted, computed, onUpdated, ref, reactive } from 'vue'

//criando o props
const props = defineProps(['courses']);

let widthDoneTrue = ref(0);

//Se as variaveis que fazem parte da computed forem atualizadas vai ser re-calculado
const coursesDone = computed(() => {

  //resumido   return courses.filter(item => item.done).length; ele já verifica se o done é true. se não tiver nada é false
  //No codigo javascript precisa add o props.nome-definido
  return widthDoneTrue.value = props.courses.filter(item => item.done === true).length;
});

onUpdated(() => {
  console.log("Cycle Updated");
  widthDoneTrue.value = props.courses.filter(item => item.done === true).length;
});

onMounted(() => {
  console.log("Cycle Mounted");
  widthDoneTrue.value = props.courses.filter(item => item.done === true).length;
});

</script>

<template>

    <!-- width:courses.length%; -->
    <!-- No template não precisa a necessidade de add props.nome-definido --> 
    <span>Progress ({{ widthDoneTrue }} / {{ courses.length }})</span>
    <div v-if="courses" :style="{'width': courses.length + '%'}" style="max-width: 400px;border:1px solid gray; border-radius: 25px; overflow: hidden ;height: 26px; background-color: red;">
        <div class="progressColor" :style="{'width': widthDoneTrue + '%'}">
            
        </div>
    </div>
    <!-- <div class="progressColor" style="width: 15%">
            
        </div> -->
    
    <!-- <div>
        {{ props }}
    </div> -->
</template>

<style>
 .progressColor {
    background-color: rgb(73, 37, 156);
    /* display: flex;
    flex-direction: row;
    align-self: flex-start; */
    height: 26px;
 }
</style>