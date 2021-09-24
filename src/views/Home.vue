<template>
  <div v-if="newQuizUser==-1" class="flex h-screen items-center justify-center bg-gray-100">

    <!-- quiz container -->
    <div class="bg-white container shadow-lg  rounded-lg px-12 py-6 flex-none relative overflow-hidden">
      <div class="absolute inset-0 overflow-hidden h-44 -top-10 -left-5 rotatebox-3">
      <img src="https://i.pinimg.com/originals/e8/97/54/e89754046d9a7481f4784fea82175a16.png" alt="" class="object-none ">

      </div>

<!-- content -->
      <div class="relative z-20">

      <!-- score container -->
      <!-- timer container -->


        <!-- soru container -->
      <div class="rounded-lg bg-gray-100 p-2 shadowbox text-center font-bold mt-8">
        <div class="bg-white p-5">
         <p class="text-xl text-gray-800 mb-3"> Welcome to the Quiz app!</p>
         <p class="text-sm text-gray-600 "> Enter your name and email address to test yourself</p>
        </div>
      </div>
      <!-- options container -->
      <div class="mt-8">

                <!-- option container -->
        <div class="shadowbox bg-gray-100 p-2 rounded-lg mb-3 relative " >
          <div class="rounded-lg font-bold flex p-2 ">
            <!-- option ID -->
            <div class="w-full">
              <input type="text" placeholder="Name" class="px-2 py-1 border border-blue-400 mb-3 rounded-md w-full">
              <input type="email" placeholder="Email" class="px-2 py-1 border border-blue-400 mb-3 rounded-md w-full">
              <button class=" bg-blue-400 hover:bg-blue-500 text-white w-20 rounded-md py-1 px-4">Next</button>
            </div>
        </div>

      </div>

      </div>
              <!-- progress container -->
        <div class="mt-8 text-center">
          <div class="h-1 w-12 bg-gray-200 rounded-full mx-auto">
          </div>
            <p class="font-bold text-gray-200">Created by Ulaş Can Demirbağ</p>
        </div>

      </div>

      <div class="absolute inset-0 overflow-hidden h-44   mt-auto" style="background: url('https://i.pinimg.com/originals/e8/97/54/e89754046d9a7481f4784fea82175a16.png') bottom;">
      </div>
    </div>
  </div>
  <div v-if="newQuizUser" class="flex h-screen items-center justify-center bg-gray-100">

    <!-- quiz container -->
    <div class="bg-white container shadow-lg  rounded-lg px-12 py-6 flex-none relative overflow-hidden">
      <div class="absolute inset-0 overflow-hidden h-44 -top-10 -left-5 rotatebox-3">
      <img src="https://i.pinimg.com/originals/e8/97/54/e89754046d9a7481f4784fea82175a16.png" alt="" class="object-none ">

      </div>

<!-- content -->
      <div class="relative z-20">

      <!-- score container -->
      <!-- timer container -->


        <!-- soru container -->
      <div class="rounded-lg bg-gray-100 p-2 shadowbox text-center font-bold text-gray-800 mt-8">
        <div class="bg-white p-5">
          Choose your exam !
        </div>
      </div>
      <!-- options container -->
      <div class="mt-8">

                <!-- option container -->
        <div class="shadowbox bg-gray-100 p-2 rounded-lg mb-3 relative option-default" @click="onExamClicked('https://opentdb.com/api.php?amount=10&category=18&difficulty=medium&type=multiple',0)" :ref="examChosen">
          <div class="rotatebox-1  bg-blue-600 rounded-md font-bold  text-white absolute right-0 -top-2 shadow-md "></div>
          <div class="rounded-lg font-bold flex p-2 ">
            <!-- option ID -->
            <div class="bg-gray-800 p-3 rounded-lg">A</div>
            <div class="flex items-center pl-6">Computers</div>
          </div>
        </div>

              <div class="shadowbox bg-gray-100 p-2 rounded-lg mb-3 relative option-default" @click="onExamClicked('https://opentdb.com/api.php?amount=10&category=23&difficulty=medium&type=multiple',1)" :ref="examChosen">
          <div class="rotatebox-1  bg-blue-600 rounded-md  font-bold  text-white absolute right-0 -top-2 shadow-md "></div>
          <div class="rounded-lg font-bold flex p-2 ">
            <!-- option ID -->
            <div class="bg-gray-800 p-3 rounded-lg">B</div>
            <div class="flex items-center pl-6">History</div>
          </div>
        </div>

              <div class="shadowbox bg-gray-100 p-2 rounded-lg mb-3 relative option-default" @click="onExamClicked('https://opentdb.com/api.php?amount=10&category=24&difficulty=medium&type=multiple',2)" :ref="examChosen">
          <div class="rotatebox-1  bg-blue-600 rounded-md  font-bold  text-white absolute right-0 -top-2 shadow-md "></div>
          <div class="rounded-lg font-bold flex p-2 ">
            <!-- option ID -->
            <div class="bg-gray-800 p-3 rounded-lg">C</div>
            <div class="flex items-center pl-6">Politics</div>
          </div>
        </div>

              <div class="shadowbox bg-gray-100 p-2 rounded-lg mb-3 relative option-default" @click="onExamClicked('https://opentdb.com/api.php?amount=10&category=27&difficulty=medium&type=multiple',3)" :ref="examChosen">
          <div class="rotatebox-1  bg-blue-600 rounded-md  font-bold  text-white absolute right-0 -top-2 shadow-md "></div>
          <div class="rounded-lg font-bold flex p-2 ">
            <!-- option ID -->
            <div class="bg-gray-800 p-3 rounded-lg">D</div>
            <div class="flex items-center pl-6">Animals</div>
          </div>
        </div>
      </div>
              <!-- progress container -->
        <div class="mt-8 text-center">
          <div class="h-1 w-12 bg-gray-200 rounded-full mx-auto">
          </div>
            <p class="font-bold text-gray-200">Created by Ulaş Can Demirbağ</p>
        </div>

      </div>

      <div class="absolute inset-0 overflow-hidden h-44   mt-auto" style="background: url('https://i.pinimg.com/originals/e8/97/54/e89754046d9a7481f4784fea82175a16.png') bottom;">
      </div>
    </div>
  </div>
  <main v-if="!newQuizUser" class="flex h-screen items-center justify-center bg-gray-100">

    <Complate v-if="endQUis" :score="score" :status="status" :clickRestart="clickRestart" :clickDone="clickDone"/>
    <!-- quiz container -->
    <div class="bg-white container shadow-lg  rounded-lg px-12 py-6 flex-none relative overflow-hidden">
      <div class="absolute inset-0 overflow-hidden h-44 -top-10 -left-5 rotatebox-3">
      <img src="https://i.pinimg.com/originals/e8/97/54/e89754046d9a7481f4784fea82175a16.png" alt="" class="object-none ">

      </div>

<!-- content -->
      <div class="relative z-20">

      <!-- score container -->
      <div class="text-right text-gray-800">
        <p class="text-sm leading-3">Score</p>
        <p class="font-bold">{{score}}</p>
      </div>
      <!-- timer container -->
        <div class="bg-gray-200 shadow-lg p-1 rounded-full w-full h-5 ">
          <div :class="`rounded-full  h-full transition-all ${timer > 91 ? 'bg-blue-700' : timer >61 ? 'bg-green-600': timer>41 ? 'bg-yellow-500' : timer>31 ? 'bg-yellow-700' : timer>11 ?'bg-red-700': timer > -1 ? 'bg-red-900':'bg-blue-700'}`" :style="`width:${timer}%;`"></div>
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
import Complate from '../components/Complate.vue'
const questionCounter=ref(0)
const timer=ref(20)
const endQUis=ref(false)
let canClick=true
let newQuizUser=ref(true)
let url =ref('')
const status = ref('')
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
let examRefs=[];
const examChosen= (el)=>{
  if(el){
    examRefs.push(el)
}
}


  let canExamCLick=true
const onExamClicked =(examUrl,index)=>{
  url.value =examUrl
  const examContainer =examRefs[index]
  if(canExamCLick){
    examContainer.classList.add('option-correct')
    examContainer.classList.remove('option-default')
     fetchQuestionsFromServer()
    setTimeout(() => {
     newQuizUser.value=false
    examContainer.classList.remove('option-correct')
    examContainer.classList.add('option-default')
    examRefs=[];
      canExamCLick=true;
    }, 1000);
  }
      canExamCLick=false;

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
  fetch(url.value)
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
   status.value='Quiz Completed !'

 }
}

const countDownTimer= ()=>{
  let interVal = setInterval(()=>{
    if(endQUis.value){
      clearInterval(interVal)
    }
    else{

      if(timer.value>0){
        timer.value--;
    }
    else{
      endQUis.value=true
      clearInterval(interVal)
      status.value='Tİme is over :('
    }
      }
  },150)
}

const clickRestart =  () => {
  questions.value=[]
   fetchQuestionsFromServer()
  setTimeout(() => {
    if(questions.value){
      endQUis.value=false
     timer.value=100
     countDownTimer()
     score.value=0
     questionCounter.value=1
     canClick=true
   }
     }, 1000);
}
const clickDone = ()=>{
  questions.value=[]
   endQUis.value=false
     timer.value=100
     countDownTimer()
     score.value=0
     questionCounter.value=0
     canClick=true
  newQuizUser.value=true
  itemsRef=[]
}


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