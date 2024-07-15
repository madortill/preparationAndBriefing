<template>
    <div id="features">
   
  
          <img src="@/assets/media/questionMark.png" alt="question-mark" class="question-mark">
      </div>
  </template>
  
  <script>

  
  
  export default {
      name: "features",
      components: {

      },
      data() {
          return {
              page: 0 ,
              showAbout: false,
              clickBtn: 0,
          };
      },
      methods: {
        
      },
  };
  
  </script>
  
  <style>
  #features {
    width: 100vw;
    height: 100vh;
  }
.question-mark{
    height: 57%;
    position: absolute;
    top: 30%;
    left: 16%;
    animation: bounce 2s linear infinite;
}

@keyframes bounce {
    20% {
        top: 30%; 
    }
    30% {
        top: 25%;
    }
    40% {
        top: 30%;
    }
    50% {
        top: 25%;

    }
    60% {
        top: 30%; 
    }
}
  
  </style>
  