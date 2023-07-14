<script setup>
import {ref,defineEmits  } from 'vue';


const props = defineProps({
  model: Object
})

const emit = defineEmits (['next-game'])

const afterGame = ref (false);
const winner = ref (false);
const loser = ref (false);

 
const nextGame = () =>{
    emit('next-game', winner.value);
    console.log(winner.value + " winner value en el emit chd")
    afterGame.value = false;
    winner.value= false;
    loser.value=false;
}
const checkAnswer = (answer) =>{
    afterGame.value = true;
  
  if (answer.correct){
   winner.value=true;
  } else {
    loser.value= true;
  }

}

 


</script>

<template>
  <div>
 
    <button v-show="afterGame" @click="nextGame()">Next question</button>
 
    <div class="question"> {{ model.question }}</div> <span v-show="loser" class="wrong">Wrong answer!</span> <span v-show="winner" class="congrats">Congrats! Thats correct!</span>
    <div :class="afterGame ? (answer.correct ? 'after-true' : 'after-false') : 'answer'" @click="checkAnswer(answer)" v-for="answer in model.answers" :key="answer.answer"> {{ answer.answer }}  </div>

  </div>

</template>

<style>
.answer{
  margin: 1rem;
  padding:0.25rem;
  border-radius: .6rem;
  border-color: rgb(5, 5, 5);
  border-style: groove;
  background-color: rgba(179, 152, 121, 0.527);
  transition: all .2s;
  cursor: pointer;
}

.answer:hover{
  transform: translateY(-3px);
  background-color: rgba(179, 152, 121, 0.342);
}
.question{
  font-family:   monospace;
  font-weight: 600;
  color: rgb(42, 49, 43);
  font-size: 4rem;

}

.after-true{
    margin: 1rem;
  padding:0.25rem;
  border-radius: .6rem;
  border-color: rgb(5, 5, 5);
  border-style: groove;
  background-color: rgba(55, 192, 37, 0.527);
  transition: all .2s;
 
}
.after-false{
    margin: 1rem;
  padding:0.25rem;
  border-radius: .6rem;
  border-color: rgb(5, 5, 5);
  border-style: groove;
  background-color: rgba(153, 47, 47, 0.527);
  transition: all .2s;
   
}
.congrats{
    color: rgba(16, 114, 3, 0.884);
    font-family:   monospace;
    font-size: 3rem;

}

.wrong{
    color: rgba(114, 16, 3, 0.884);
    font-family:   monospace;
    font-size: 3rem;

}
</style>