<template>
  <main class="flex h-screen items-center justify-center bg-gray-100">

    <Complate v-if="endQUis"/>
    <!-- quiz container -->
    <div class="bg-white container shadow-lg  rounded-lg px-12 py-6 flex-none relative overflow-hidden">
      <div class="absolute inset-0 overflow-hidden h-44 -top-10 -left-5 rotatebox-3">
      <img src="https://i.pinimg.com/originals/e8/97/54/e89754046d9a7481f4784fea82175a16.png" alt="" class="object-none ">

      </div>

<!-- content -->
      <div class="relative z-20">

      <!-- score container -->
      <div class="text-right text-gray-800">
        <p class="text-sm leading-3">Skor</p>
        <p class="font-bold">{{score}}</p>
      </div>
      <!-- timer container -->
        <div class="bg-gray-200 shadow-lg p-1 rounded-full w-full h-5 ">
          <div class=" bg-blue-700 rounded-full  h-full" :style="`width:${timer}%;`"></div>
        </div>


        <!-- soru container -->
      <div class="rounded-lg bg-gray-100 p-2 shadowbox text-center font-bold text-gray-800 mt-8">
        <div class="bg-white p-5">
          {{currentQuestion.question}}
        </div>
      </div>
      <!-- options container -->
      <div class="mt-8">

                <!-- option container -->
                <div v-for="(choice,index) in currentQuestion.choices" :key="index">
        <div class="shadowbox bg-gray-100 p-2 rounded-lg mb-3 relative option-default" @click="onOptionClicked(choice,index)" :ref="optionChosen">
          <div class="rotatebox-1  bg-blue-600 rounded-md w-10 h-10 p-1 font-bold  text-white absolute right-0 -top-2 shadow-md"><p class="rotatebox-2">+10</p></div>
          <div class="rounded-lg font-bold flex p-2 ">
            <!-- option ID -->
            <div class="bg-gray-800 p-3 rounded-lg">{{index==0 ? 'A' : index ==1 ? 'B' : index==2 ? 'C' :'D'}}</div>
            <div class="flex items-center pl-6">{{choice}}</div>
          </div>
        </div>
                </div>
   


        <!-- option container -->
     




      </div>

              <!-- progress container -->
        <div class="mt-8 text-center">
          <div class="h-1 w-12 bg-gray-200 rounded-full mx-auto">
          </div>
            <p class="font-bold text-gray-200">{{questionCounter}}/{{questions.length}}</p>
        </div>

      </div>



      <div class="absolute inset-0 overflow-hidden h-44   mt-auto" style="background: url('https://i.pinimg.com/originals/e8/97/54/e89754046d9a7481f4784fea82175a16.png') bottom;">
      </div>
    </div>
  </main>
</template>

<script setup>
import { ref } from "@vue/reactivity";
import { onMounted } from "@vue/runtime-core";
import Complate from '../components/Complate.vue'
const questionCounter=ref(0)
const timer=ref(20)
const endQUis=ref(false)
let canClick=true
let score=ref(0)
const currentQuestion=ref({
  question:"",
  answer:1,
  choices:[]
})

let questions=ref([])
let itemsRef=[];
const optionChosen= (el)=>{
  if(el){
    itemsRef.push(el)
}
}
const onOptionClicked= (choice,index)=>{
  if(canClick){
    const divContainer= itemsRef[index]
    if(currentQuestion.value.answer==(index+1)){
      score.value+=10
          divContainer.classList.add('option-correct')
          divContainer.classList.remove('option-default')
      }else{
                divContainer.classList.add('option-wrong')
          divContainer.classList.remove('option-default')
      }
      
      clearSelected(divContainer)
      timer.value=100
      canClick=false;
  }

}

const fetchQuestionsFromServer= async function(){
  fetch('https://opentdb.com/api.php?amount=10&category=11&difficulty=easy')
  .then((res)=>{
    return res.json()
  }).then((data)=>{
    const newQuestions=data.results.map((serverQuestion)=>{
      const arrangedQuestion = {
        question:serverQuestion.question,
        choices:'',
        answer:''
      }
      const choices = serverQuestion.incorrect_answers;

      arrangedQuestion.answer=Math.floor(Math.random()*4+1);
      choices.splice(arrangedQuestion.answer-1,0,serverQuestion.correct_answer)
      arrangedQuestion.choices=choices
      return arrangedQuestion
    })
    console.log(newQuestions);
    questions.value=newQuestions
      loadQuestion()
       countDownTimer()
  })
}

const clearSelected=(selected)=>{
  setTimeout(() => {
    selected.classList.remove('option-correct')
    selected.classList.remove('option-wrong')
    selected.classList.add('option-default')
    loadQuestion()
  }, 1000);
}

const loadQuestion= () => {
 if(questions.value.length>questionCounter.value){
    currentQuestion.value=questions.value[questionCounter.value]
    questionCounter.value++;
    canClick=true
    timer.value=100
}
else{
   endQUis.value=true
 }
}

const countDownTimer= ()=>{
  let interVal = setInterval(()=>{
    if(timer.value>0){
      timer.value--;
    }
    else{
      console.log('timer is up');
      clearInterval(interVal)
    }
  },150)
}

onMounted(()=>{
  fetchQuestionsFromServer()
})
</script>

<style scoped>
.shadowbox{
  box-shadow: 6px 6px 18px rgba(0, 0, 0, 0.09),-6px -6px 18px #ffffff;
}
.rotatebox-1{
  transform: rotate(45deg);
}
.rotatebox-2{
  transform: rotate(-45deg);
}
.rotatebox-3{
  transform: rotate(-5deg);
}
.container{
  max-width: 400px;
  border-radius: 25px;
}
</style>