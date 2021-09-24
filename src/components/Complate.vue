<template>
<div class="flex justify-center items-center w-screen h-screen absolute z-30 bg-gray-800 bg-opacity-70">
    <div class="text-white font-bold bg-blue-500 text-center p-4 rounded-md">
        <p class="text-2xl">{{status}}</p>
        <p class="text-3xl my-4">Score:{{score}}%  {{ Number(score)==50 ? 'Mediocre' : Number(score) >50 ? 'Good' : 'Bad'  }}</p>
        <div class="flex justify-between">
            <div class="rounded-full py-1 mr-2 w-28  bg-blue-400 cursor-pointer hover:text-black hover:bg-white">Done</div>
            <div class="rounded-full py-1  w-28 cursor-pointer bg-blue-400  hover:text-black hover:bg-white" @click='clickRestart'>Restart</div>
        </div>
    </div>
</div>
</template>
<script>
export default{
    props:['status','score','clickRestart']
}
</script>