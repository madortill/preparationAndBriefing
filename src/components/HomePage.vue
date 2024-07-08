<template>
    <div id="home-page">
      <div v-if="partNum < 5" class="white-window">
        <div class="center-text" v-if="partNum === 0">
          <p class="explain-text pos-start-text">
            בלומדה זו נתמקד ב-2 השלבים הראשונים ממעגל החניכה: הכנה עצמית ותדרוך.
          </p>
        </div>
  
        <div class="center-text" v-if="partNum === 1 || partNum === 2">
          <img src="../../src/assets/media/bell.svg" class="bell" alt="bell" />
          <p class="explain-text">תזכורת למעגל החניכה:</p>
  
          <!-- the circles -->
          <div class="circle-container">
            <div
              v-for="(item, index) in arrayAgo"
              :key="index"
              class="circle"
              :class="getCircleClass(index)"
            >
              {{ arrayAgo[index] }}
            </div>
          </div>
          <!-- the arrows -->
          <img
            v-for="i in 5"
            :key="i"
            class="arrow"
            :class="getArrowClass(i)"
            src="../../src/assets/media/arrow.svg"
          />
  
          <!-- the openning window -->
          <div v-if="partNum === 2">
            <!-- the blur bg -->
            <div class="hide-bg"></div>
            <div class="jumping-window">
              <p  class="adjust">שלבי הכנה עצמאית ועיבוד הם שלבים עצמאים של החונך.</p>
              <button id="expBtn" style="height: 30%;" class="startBtn posCenterBtn" @click="nextPart">
                הבא
              </button>
            </div>
          </div>
        </div>
  
        <div v-if="partNum === 3" class="finale-exe">
          <p
            v-for="(text, index) in array1"
            :key="text"
            :class="{
              'talk-text': index === 0 || index === 2,
              'info-text-goal': index !== 0 && index !== 2,
            }"
            :style="{
              'font-size': index === 0 || index === 2 ? '3rem' : '1.6rem',
            }"
          >
            {{ text }}
          </p>      
          </div>
  
        <div v-if="partNum === 4">
          <div class="explain-page center-text">
            <p class="explain-text">{{ explainArray[0] }}</p>
            <p class="talk-text">הכנה עצמית</p>
            <p class="explain-text">{{ explainArray[1] }}</p>
            <p style="font-size: 2.3rem; color: #4b7189">בהצלחה!</p>
          </div>
        </div>
  
        <button
          v-if="partNum !== 2"
          id="expBtn"
          class="startBtn"
          :class="partNum === 1 || partNum === 3 ? 'posLeftBtn' : 'posCenterBtn'"
          @click="nextPart"
        >
          הבא
        </button>
      </div>
  
      <div v-if="partNum > 4">
        <div v-if="!showQuestions">
          <navbar v-if="showNav" :titleIndex="titleIndex"></navbar>
          <information-page
            :titleIndex="titleIndex"
            @move-sub="moveSub"
            @close-nav="closeNav"
          ></information-page>
        </div>
        <div v-if="showQuestions">
          <quick-questions
            :indexQuestion="indexQuestion"
            @next-sub="nextSub"
          ></quick-questions>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import Navbar from "@/components/Navbar.vue";
  import InformationPage from './InformationPage.vue';
  
  export default {
    name: "home-page",
    components: {
      Navbar,
      InformationPage,
    },
  
    data() {
      return {
        partNum: 0,
        showInfo: true,
        index: 0,
        showGoal: false,
        showExplain: true,
        titleIndex: 0,
        showNav: true,
        showQuestions: false,
        showInformation: false,
        indexQuestion: 0,
        array1: [
          "מטרת על",
          'החניך יבצע הכנה עצמית ויתדרך לביצוע עפ"י העקרונות שנלמדו.',
          "מטרות ביניים",
          "החניך יציין את שלבי מעגל החניכה.",
          "החניך יפרט את תחומי ההכנה העצמית.",
          "החניך יסביר את מטרות התדריך, עקרונותיו ודגשיו.",
          "החניך יתרגל תדריך לקראת תצפית.",
        ],
        explainArray: [
          "נתחיל בנושא הראשון במעגל החניכה",
          "אם הינך בטוח/ה שרוצה להמשיך בלמידת החומר לחצ/י המשך",
        ],
        arrayAgo: ["משוב", "עיבוד", "תצפית", "תדריך", "הכנה עצמית"],
      };
    },
  
    methods: {
      nextPart() {
        this.partNum++;
      },
      nextSub() {
        this.showQuestions = false;
        console.log(this.titleIndex);
        if (this.titleIndex === 4) {
          this.$emit("next-page");
        }
      },
      moveSub(showQ) {
        console.log(showQ);
        this.showQuestions = false;
  
        if (showQ === true) {
          this.showQuestions = true;
          this.indexQuestion++;
        } else {
          this.showQuestions = false;
        }
  
        if (this.titleIndex >= 0 && this.titleIndex <= 4) {
          this.titleIndex++;
        }
      },
      closeNav() {
        this.showNav = false;
      },
      getCircleClass(index) {
        return "circle" + index;
      },
      getArrowClass(index) {
        return "arrow" + index;
      },
    },
  };
  </script>
  
  <style>
  #home-page {
    background-color: #f2f2f2;
    width: 100vw;
    height: 100vh;
    display: flex;
    position: relative;
    justify-content: center;
  }
  
  .jumping-window {
    background-color: white;
    width: 100%;
    height: 30%;
    position: absolute;
    top: 50%;
    left: 0%;
    transform: translateY(-50%);
  }
  
  .adjust {
      font-weight: bold;
      font-size: 1.2rem;
      position: absolute;
      top: 20%;
      left:50%;
      transform: translateX(-50%);
      width:100%;
  }
  
  .bell {
    position: absolute;
    top: -5%;
    right: 22%;
    display: block;
    width: 40px;
    height: 40px;
    font-size: 40px;
    margin: 50px auto 0;
    color: #9e9e9e;
    -webkit-animation: ring 4s 0.7s ease-in-out infinite;
    -webkit-transform-origin: 50% 4px;
    -moz-animation: ring 4s 0.7s ease-in-out infinite;
    -moz-transform-origin: 50% 4px;
    animation: ring 4s 0.7s ease-in-out infinite;
    transform-origin: 50% 4px;
  }
  
  @-webkit-keyframes ring {
    0% {
      -webkit-transform: rotateZ(0);
    }
    1% {
      -webkit-transform: rotateZ(30deg);
    }
    3% {
      -webkit-transform: rotateZ(-28deg);
    }
    5% {
      -webkit-transform: rotateZ(34deg);
    }
    7% {
      -webkit-transform: rotateZ(-32deg);
    }
    9% {
      -webkit-transform: rotateZ(30deg);
    }
    11% {
      -webkit-transform: rotateZ(-28deg);
    }
    13% {
      -webkit-transform: rotateZ(26deg);
    }
    15% {
      -webkit-transform: rotateZ(-24deg);
    }
    17% {
      -webkit-transform: rotateZ(22deg);
    }
    19% {
      -webkit-transform: rotateZ(-20deg);
    }
    21% {
      -webkit-transform: rotateZ(18deg);
    }
    23% {
      -webkit-transform: rotateZ(-16deg);
    }
    25% {
      -webkit-transform: rotateZ(14deg);
    }
    27% {
      -webkit-transform: rotateZ(-12deg);
    }
    29% {
      -webkit-transform: rotateZ(10deg);
    }
    31% {
      -webkit-transform: rotateZ(-8deg);
    }
    33% {
      -webkit-transform: rotateZ(6deg);
    }
    35% {
      -webkit-transform: rotateZ(-4deg);
    }
    37% {
      -webkit-transform: rotateZ(2deg);
    }
    39% {
      -webkit-transform: rotateZ(-1deg);
    }
    41% {
      -webkit-transform: rotateZ(1deg);
    }
  
    43% {
      -webkit-transform: rotateZ(0);
    }
    100% {
      -webkit-transform: rotateZ(0);
    }
  }
  
  @-moz-keyframes ring {
    0% {
      -moz-transform: rotate(0);
    }
    1% {
      -moz-transform: rotate(30deg);
    }
    3% {
      -moz-transform: rotate(-28deg);
    }
    5% {
      -moz-transform: rotate(34deg);
    }
    7% {
      -moz-transform: rotate(-32deg);
    }
    9% {
      -moz-transform: rotate(30deg);
    }
    11% {
      -moz-transform: rotate(-28deg);
    }
    13% {
      -moz-transform: rotate(26deg);
    }
    15% {
      -moz-transform: rotate(-24deg);
    }
    17% {
      -moz-transform: rotate(22deg);
    }
    19% {
      -moz-transform: rotate(-20deg);
    }
    21% {
      -moz-transform: rotate(18deg);
    }
    23% {
      -moz-transform: rotate(-16deg);
    }
    25% {
      -moz-transform: rotate(14deg);
    }
    27% {
      -moz-transform: rotate(-12deg);
    }
    29% {
      -moz-transform: rotate(10deg);
    }
    31% {
      -moz-transform: rotate(-8deg);
    }
    33% {
      -moz-transform: rotate(6deg);
    }
    35% {
      -moz-transform: rotate(-4deg);
    }
    37% {
      -moz-transform: rotate(2deg);
    }
    39% {
      -moz-transform: rotate(-1deg);
    }
    41% {
      -moz-transform: rotate(1deg);
    }
  
    43% {
      -moz-transform: rotate(0);
    }
    100% {
      -moz-transform: rotate(0);
    }
  }
  
  @keyframes ring {
    0% {
      transform: rotate(0);
    }
    1% {
      transform: rotate(30deg);
    }
    3% {
      transform: rotate(-28deg);
    }
    5% {
      transform: rotate(34deg);
    }
    7% {
      transform: rotate(-32deg);
    }
    9% {
      transform: rotate(30deg);
    }
    11% {
      transform: rotate(-28deg);
    }
    13% {
      transform: rotate(26deg);
    }
    15% {
      transform: rotate(-24deg);
    }
    17% {
      transform: rotate(22deg);
    }
    19% {
      transform: rotate(-20deg);
    }
    21% {
      transform: rotate(18deg);
    }
    23% {
      transform: rotate(-16deg);
    }
    25% {
      transform: rotate(14deg);
    }
    27% {
      transform: rotate(-12deg);
    }
    29% {
      transform: rotate(10deg);
    }
    31% {
      transform: rotate(-8deg);
    }
    33% {
      transform: rotate(6deg);
    }
    35% {
      transform: rotate(-4deg);
    }
    37% {
      transform: rotate(2deg);
    }
    39% {
      transform: rotate(-1deg);
    }
    41% {
      transform: rotate(1deg);
    }
  
    43% {
      transform: rotate(0);
    }
    100% {
      transform: rotate(0);
    }
  }
  
  .explain-page {
    position: absolute;
    top: 10%;
  }
  
  .finale-exe {
    position: absolute;
    top: 5%;
  }
  
  .arrow {
    width: 4rem;
    position: absolute;
  }
  
  .arrow1 {
    top: 30%;
    right: 30%;
    transform: rotate(150deg);
  }
  
  .arrow2 {
    top: 30%;
    left: 30%;
    transform: rotate(100deg);
  }
  
  .arrow3 {
    bottom: 35%;
    left: 20%;
    transform: rotate(-10deg);
  }
  
  .arrow4 {
    bottom: 15%;
    left: 45%;
    transform: rotate(-60deg);
  }
  
  .arrow5 {
    bottom: 35%;
    right: 20%;
    transform: rotate(240deg);
  }
  
  .circle {
    width: 100%;
    height: 7rem;
    border-radius: 50%;
    text-align: center;
    color: white;
    font-size: 1.5rem;
    font-weight: 550;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 1.6%;
    transition: all 0.3s ease;
    /* animation: floatAnimation 3s ease-in-out infinite; */
    box-shadow: 0 5px 7px rgba(0, 0, 0, 0.2);
    background-color: #eb5781;
  }
  
  .circle:hover {
    box-shadow: 0 15px 9px rgba(0, 0, 0, 0.4);
    width: 8rem;
    height: 8rem;
    padding: 2%;
    /* cursor: pointer; */
  }
  
  .circle-container {
    position: absolute;
    top: 20%;
    left: 50%;
    transform: translateX(-50%);
    width: 100%; /* Adjust the width to fit your design */
    height: 70%; /* Adjust the height to fit your design */
    margin: auto; /* Center the container */
    display: grid;
    grid-template-columns: repeat(7, 14.3%);
    grid-template-rows: repeat(5, 20%);
  }
  
  .circle0 {
    grid-column-start: 6;
    grid-row-start: 2;
    position: relative;
  }
  
  .circle1 {
    grid-column-start: 5;
    grid-row-start: 4;
  }
  
  .circle2 {
    grid-column-start: 3;
    grid-row-start: 4;
  }
  
  .circle3 {
    grid-column-start: 2;
    grid-row-start: 2;
  }
  
  .circle4 {
    grid-column-start: 4;
    grid-row-start: 0;
  }
  
  @keyframes floatAnimation {
    0% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(-8px);
    }
    100% {
      transform: translateY(0);
    }
  }
  
  .posCenterBtn {
    position: absolute;
    bottom: 5%;
    left: 50%;
    transform: translateX(-50%);
  }
  .posLeftBtn {
    position: absolute;
    bottom: 5%;
    left: 7%;
  }
  
  
  
  .startBtn {
    border: none;
    cursor: pointer;
    width: 15%;
    height: 7%;
    color: #ffffff;
    background-color: #ff87ab;
    font-size: 1.6rem;
    border-radius: 100px;
    min-width: 12%;
  }
  .startBtn {
    animation: borderPulse 4000ms infinite ease-out;
  }
  
  .startBtn:hover,
  .startBtn:focus {
    animation: borderPulse 4000ms infinite ease-out, hoverShine 200ms;
  }
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
  /* Declare border pulse animation */
  
  .white-window {
    position: absolute;
    width: 40%;
    height: 70%;
    left: 30%;
    bottom: 20%;
    background: #fff;
    border-radius: 3rem;
    box-shadow: 0 15px 20px -20px rgba(0, 0, 0, 0.4);
  }
  
  .hide-bg {
    position: absolute;
    bottom: 0%;
    background: #c7c5c5;
    opacity: 0.8;
    width: 100%;
    height: 100%;
  }
  
  .explain-text {
    font-size: 2.1rem;
    padding: 1.5% 7% 2%;
    color: rgb(79, 77, 77);
    margin: 0%;
  }
  
  .pos-start-text {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    width: 100%;
  }
  
  .center-text {
    text-align: center;
  }
  
  .goalBtn {
    position: absolute;
    bottom: 5%;
    left: 5%;
  }
  .info-text-goal {
    background-color: none;
    border-radius: 30px;
    height: 6%;
    transition: background-color 0.3s ease;
    margin: 3%;
  }
  .info-text-goal:hover {
    background-color: #dbdbdb;
  }
  /* 
  .talk-text {
    margin: 3%;
    animation: floatAnimation 3s ease-in-out infinite;
    color: #ff5d8f;
    font-size: 3rem;
    border-radius: 10px;
    top: 1.5%;
    text-decoration: none;
    position: relative;
    cursor: default;
    &:hover {
      color: #ff5d8f;
  
      &:before {
        visibility: visible;
        transform: scaleX(1);
      }
    }
  
    &:before {
      content: "";
      position: absolute;
      width: 40%;
      height: 2px;
      bottom: 0;
      right: 30%;
      background-color: #ff5d8f;
      visibility: hidden;
      transform: scaleX(0);
      transition: all 0.3s ease-in-out 0s;
    } */
  /* } */
  </style>
  