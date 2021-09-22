<template>
  <main class="flex h-screen items-center justify-center bg-gray-100">
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
        <p class="font-bold">60</p>
      </div>
      <!-- timer container -->
        <div class="bg-white shadow-lg p-1 rounded-full w-full h-5 ">
          <div class=" bg-blue-700 rounded-full w-11/12 h-full"></div>
        </div>


        <!-- soru container -->
      <div class="rounded-lg bg-gray-100 p-2 shadowbox text-center font-bold text-gray-800 mt-8">
        <div class="bg-white p-5">
          Kim en güçlü marvel karakteridir ?
        </div>
      </div>
      <!-- options container -->
      <div class="mt-8">
        <!-- option container -->
        <div class="shadowbox bg-gray-100 p-2 rounded-lg mb-3">
          <div class="bg-white rounded-lg font-bold flex p-2">
            <!-- option ID -->
            <div class="bg-gray-400 p-3 rounded-lg">A</div>
            <div class="flex items-center pl-6">Thor</div>
          </div>
        </div>
                <!-- option container -->
        <div class="shadowbox bg-gray-100 p-2 rounded-lg mb-3">
          <div class="bg-red-600 rounded-lg font-bold flex p-2 text-white">
            <!-- option ID -->
            <div class="bg-gray-800 p-3 rounded-lg">B</div>
            <div class="flex items-center pl-6">Doctor Strange</div>
          </div>
        </div>
                <!-- option container -->
        <div class="shadowbox bg-gray-100 p-2 rounded-lg mb-3 relative">
          <div class="rotatebox-1  bg-blue-600 rounded-md w-10 h-10 p-1 font-bold  text-white absolute right-0 -top-2 shadow-md"><p class="rotatebox-2">+10</p></div>
          <div class="bg-green-600 rounded-lg font-bold flex p-2 text-white">
            <!-- option ID -->
            <div class="bg-gray-800 p-3 rounded-lg">C</div>
            <div class="flex items-center pl-6">Ms Marvel</div>
          </div>
        </div>

        <!-- option container -->
        <div class="shadowbox bg-gray-100 p-2 rounded-lg mb-3">
          <div class="bg-white rounded-lg font-bold flex p-2">
            <!-- option ID -->
            <div class="bg-gray-400 p-3 rounded-lg">D</div>
            <div class="flex items-center pl-6">Hulk</div>
          </div>
        </div>




      </div>

              <!-- progress container -->
        <div class="mt-8 text-center">
          <div class="h-1 w-12 bg-gray-800 rounded-full mx-auto">
          </div>
            <p class="font-bold text-gray-800">2/10</p>
        </div>

      </div>

    </div>
  </main>
</template>

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