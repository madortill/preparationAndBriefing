<template>
    <div id="open-screen">
      <h1 class="text-title">לומדת הכנה עצמית ותדריך</h1>
      <button class="btnNext" @click="startTutorial">התחל</button>
      <div class="animation-part"></div>
    </div>
  </template>
  
  <script>
  export default {
    name: "open-screen",
    components: {},
    data() {
      return {};
    },
    methods: {
      startTutorial() {
        this.$emit("next-page");
      },
    },
  };
  </script>
  
  <style scoped>
  #open-screen {
    background-size: 100vw 100vh;
    direction: rtl;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
    background-color: #ebebeb;
    flex-direction: column;
  }
  

  .text-title {
    color: rgb(83, 82, 82);
    font-family: "Heebo-Bold";
    font-size: 7rem;
    /* floatAnimation 3s ease-in-out infinite; */
    animation: floatAnimation 3s ease-in-out infinite;
    width: 50rem;
    text-align: center;
  }
  
  .btnNext {
    border: none;
    cursor: pointer;
    height: 4rem;
    font-size: 2rem;
    color: #ffffff;
    border-radius: 100px;
    background-color: #ff87ab;
    min-width: 9rem;
  }
  
  .btnNext {
    animation: borderPulse 4000ms infinite ease-out;
  }
  
  .btnNext:hover,
  .btnNext:focus {
    animation: borderPulse 4000ms infinite ease-out, hoverShine 200ms;
  }
  
  /* Declare border pulse animation */
  @keyframes borderPulse {
    0% {
      box-shadow: inset 0px 0px 0px 5px rgba(255, 255, 255, 0.4),
        0px 0px 0px 0px rgba(255, 255, 255, 1);
    }
    35% {
      box-shadow: inset 0px 0px 0px 3px rgba(117, 117, 255, 0.2),
        0px 0px 0px 10px rgba(255, 255, 255, 0);
    }
    50% {
      box-shadow: inset 0px 0px 0px 5px rgba(255, 255, 255, 0.4),
        0px 0px 0px 0px rgba(255, 255, 255, 1);
    }
    75% {
      box-shadow: inset 0px 0px 0px 3px rgba(117, 117, 255, 0.2),
        0px 0px 0px 10px rgba(255, 255, 255, 0);
    }
    100% {
      box-shadow: inset 0px 0px 0px 5px rgba(255, 255, 255, 0.4),
        0px 0px 0px 0px rgba(255, 255, 255, 1);
    }
  }
  
  @keyframes hoverShine {
    0% {
      background-image: linear-gradient(
        135deg,
        rgba(255, 255, 255, 0.4) 0%,
        rgba(255, 255, 255, 0) 50%,
        rgba(255, 255, 255, 0) 100%
      );
    }
    50% {
      background-image: linear-gradient(
        135deg,
        rgba(255, 255, 255, 0) 0%,
        rgba(255, 255, 255, 0.4) 50%,
        rgba(255, 255, 255, 0) 100%
      );
    }
    100% {
      background-image: linear-gradient(
        135deg,
        rgba(255, 255, 255, 0) 0%,
        rgba(255, 255, 255, 0) 50%,
        rgba(255, 255, 255, 0.4) 100%
      );
    }
  }
  
  @keyframes floatAnimation {
    0% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(-12px);
    }
    100% {
      transform: translateY(0);
    }
  }
  </style>
  