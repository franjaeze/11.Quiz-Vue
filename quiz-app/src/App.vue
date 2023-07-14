<script setup>
import Track from './components/track.vue';
import { ref,reactive } from 'vue';

const index = ref(0);
const score = reactive({
      correctAnswer: 0,
      totalAnswer: 0,
    })
const nextTrack = (winner) => {
  console.log(winner + ' winner value en el parnt')
  if(winner){
    score.correctAnswer++;
    score.totalAnswer++;
  } else {
    score.totalAnswer++;
  }
  index.value++;
}


const tracks = [{
    question: "What is Vue?",
    answers: [  {  answer: "An open-source, progressive Javascript framework for building user interfaces that aim to be incrementally adoptable", correct: true },
    {  answer: "An open-source JavaScript library that is used for building user interfaces specifically for single-page applications", correct: false }, 
    {  answer: "Supported by Google, is an open-source, JS-based software engineering platform for building user interfaces (front-end)", correct: false }, 
    {  answer: "A modern JS framework used to build static web apps. You can use It to build single, reusable components for projects of any kind", correct: false },   ]
},
{
    question: "What are the major features of VueJS?",
    answers: [  {  answer: "Virtual DOM, Components, JSX, Simplicity, Performance", correct: false },
    {  answer: "Custom Components, Data Binding, Dependency Injection, Testing, Comprehensive, Browser Compatibility", correct: false }, 
    {  answer: "Virtual DOM, Components, Templates, Routing, Light weight", correct: true }, 
    {  answer: "Easy Sintax, fast modules, big partnerships", correct: false },   ]
},
{
    question: "What are the lifecycle methods of VueJS?",
    answers: [  {  answer: "Creation(Initialization), Mounted, Updating, Destruction", correct: true },
    {  answer: " Mounted, Creation(Initialization), Updating, Destruction", correct: false }, 
    {  answer: "Creation(Initialization), Updating, Destruction, Mounted", correct: false }, 
    {  answer: "Creation(Initialization), Updating, , Mounted, Destruction", correct: false },   ]
},
{
    question: "What is Vue?",
    answers: [  {  answer: "An open-source, progressive Javascript framework for building user interfaces that aim to be incrementally adoptable", correct: true },
    {  answer: "An open-source JavaScript library that is used for building user interfaces specifically for single-page applications", correct: false }, 
    {  answer: "Supported by Google, is an open-source, JS-based software engineering platform for building user interfaces (front-end)", correct: false }, 
    {  answer: "A modern JS framework used to build static web apps. You can use It to build single, reusable components for projects of any kind", correct: false },   ]
},









]

const game = ref(false);
 const startGame = () => {
  game.value = true;
 }

  

</script>

<template>
  <div>
    <h1 class="title"><span v-if="!game">Welcome to quiz App</span> <span v-else > Score {{ score.correctAnswer}} / {{ score.totalAnswer }}</span></h1>
    <button @click="startGame()" v-show="!game">Start!</button>
 
    <Track v-if="game"
           :model="tracks[index]"
           @next-game="nextTrack"
           
           />
  </div>

</template>

<style>
h1 span{
 background: rgb(242,234,30);
background: linear-gradient(183deg, rgba(242,234,30,1) 0%, rgba(182,111,22,1) 39%, rgba(187,59,29,1) 73%, rgba(29,113,187,1) 97%);
Background-clip:text; 
-webkit-background-clip:text; 
Color:transparent; 
letter-spacing: .5rem;
 
} 

button{
  border-style: solid;
  border-color: black;
  background-color: rgba(77, 74, 70, 0.4);
  box-shadow: rgba(50, 50, 93, 0.25) 0px 50px 100px -20px, rgba(0, 0, 0, 0.3) 0px 30px 60px -30px, rgba(10, 37, 64, 0.35) 0px -2px 6px 0px inset;
  transition: all .6s;
}

button:hover{
  box-shadow: rgba(170, 161, 80, 0.25) 0px 50px 100px -20px, rgba(218, 160, 160, 0.3) 0px 30px 60px, rgba(120, 172, 224, 0.35)  0px -2px 6px 0px inset;
  transform: translateY(-5px);
 
}
button:active{
  box-shadow: rgba(170, 161, 80, 0.25) 25px 50px 100px -20px, rgba(218, 160, 160, 0.3) 0px 30px 60px, rgba(120, 172, 224, 0.35)  0px -2px 6px 0px inset;
  transform: translateY(3px);
  transform: translatex(1px);
  background-color: rgba(77, 74, 70, 0.6);

 
}

 
</style>
