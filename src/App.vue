<script setup>

import { ref, reactive } from 'vue';

//No COMPOSITION API não precisa declarar o componente importa em components
//já no OPTIONS API precisa declarar para usar
import ProgressComp from './components/ProgressComp.vue';

//com vite vue - composition api precisa criar um ref 
//Para quye quando ocorra uma alteração em uma variavel sejá reativo
//e em seguida já seja renderizado novamente o valor
// com projeto normal de vue que é o options api ele já é reativo

//usado para tipos primitivos string, NUMEROS ... 
let count = ref(0);
//quando criar uma variavel com ref 
//fica dentro de value 
//EXEMPLO count.value = receber o valor aqui

//reactive É UTILIZADO PARA objetos

let courses = reactive([
  {
   title: "Javascript",
   done: true
  },
  {
   title: "Angular",
   done: true
  },
  {
   title: "flutter",
   done: false
  },
  {
   title: "React native",
   done: false
  },
  {
   title: "Ionic",
   done: true
  },
  {
   title: "Laravel",
   done: false
  },
  {
   title: "React Js",
   done: true
  },
  {
   title: "Next js",
   done: false
  },
  {
   title: "Nest js",
   done: true
  },
  {
   title: "Node js",
   done: true
  },
  {
   title: "Code igniter js",
   done: true
  }
]);

let newCourse = reactive({
  title: '',
  done: false
});

function incrementCount() {
  count.value++;
  //console.log(count.value)
}

// function limparLista() {
//   courses = [];
// }

function addNovoCurso() {
  
  if(newCourse.title != '') {
    courses.push({title: newCourse.title});
    newCourse.title = '';
    newCourse.done = false;
  }

}

// function doneTrueMethod() {
  
//   let totalDoneTrue = 0;

//   for(let i = 0; i < courses.length; i++) {
//     if(courses[i].done === true) {
//       totalDoneTrue++;
//     }
//   }

//   return totalDoneTrue;
// }

</script>

<template>
  <!-- no template não precisa add count.value quando cria a variavel como ref somente passa  o valor -->
  <div>
    Olá Vite
  </div>
  <h2>Contador:</h2>
  <h2>{{ count }}</h2>
  <button @click="incrementCount()"> Incrementar + </button>

  <br>

  <div style="margin-top: 32px; margin-bottom: 32px;">
    <ProgressComp :courses="courses" />
  </div>
  
  <div>
    <ul v-if="courses.length > 0">
      <li v-for="course in courses" :key="course.title" :style="{'text-decoration-line' : (course.done ? 'line-through' : '')}">
       {{ course.title }}
      </li>
    </ul>
  </div>

  <div>
    <input type="text" v-model="newCourse.title">
    <button style="margin-left: 16px;" @click="addNovoCurso()">Adicionar curso</button>
  </div>

  <!-- <div>
    <button style="margin-left: 16px;" @click="limparLista()">Excluir Lista</button>
  </div> -->

</template>

<style scoped>

</style>
