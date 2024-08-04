<template>
  <div id="end-screen">
    <div class="white-window">
      <div v-if="part === 0">
        <p class="headline-text">{{ summaryArray[0] }}</p>
        <div class="the-type-writer type-writer">
          <p
            v-for="(text, index) in summaryArray.slice(1)"
            :key="text"
            :style="{
              '--delay': `${index * 3.2}s`,
              '--width': `${text.length}ch`,
            }"
            class="explain-text"
          >
            {{ text }}
          </p>
        </div>
        <button 
        v-if="showBtn"
      class="nextBtn"
      @click="nextPart"
    >
      הבא
    </button>
      </div>
      <div class="adjust-size" :class="!showFade ? 'fade-in-animation' : ''" v-if="part === 1 || part === 2">
<p :class="showFade ? 'fade-in-out-animation' : 'fade-in'" class="the-text">{{ text }}</p>
<p v-if="part === 2" class="tat-text">סיימת בהצלחה את הלומדה!!</p>
      </div>
    </div>
    <div class="black-square" v-show="part === 1"> </div>
    <confetti v-show="part === 2"></confetti>

  </div>
</template>

<script>
import Confetti from './Confetti.vue';
export default {
  name: "end-screen",
  components: {Confetti},
  data() {
    return {
        showFade: true,
      showBtn: false,
      part: 0,
      text: 'ו . . .',
      summaryArray: [
        "אז מה למדנו?",
        "בלומדה זו למדנו על השלב הראשון במעגל החניכה: הכנה עצמית ותדריך.",
        "עברנו על ההכנה העצמית שלנו עם עצמנו כחונכים וכיצד יש להעביר תדריך.",
        'עכשיו, אתם מוכנים להתקדם לשלב הבא "תצפית".',
      ],
    };
  },
  mounted() {
let timer =  setTimeout(()=> {
this.showBtn = true;
    clearTimeout(timer);
}, 9600);
  },
  methods: {
    nextPart() {
        this.part++;
        this.showFade = true;
        let timer =  setTimeout(()=> {
            this.part++;
            this.text = 'כ ל      ה כ ב ו ד';
            this.showFade = false;
            clearTimeout(timer);
        }, 4000);
        
    },
  },
};
</script>

<style scoped>
#end-screen{
    width: 100vw;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center
}

.black-square {
    background-color: black;
    width: 100vw;
    height: 100vh;
    position: absolute;
    animation: fade 4s linear;

}
.white-window {
  width: 40rem;
  height: 25rem;
  background: #fff;
  border-radius: 3rem;
  box-shadow: 0 15px 20px -20px rgba(0, 0, 0, 0.4);
  padding: 1.5rem;
}

.adjust-size {
    /* width: 100%;
  height: 100%; */
}
/* typewriter */

.type-writer > p {
  animation: typeWrite 2s var(--delay) steps(44) normal both,
    blink 400ms var(--delay) steps(45) 5;
}

.the-type-writer > p {
  display: block;
  width: fit-content;
  white-space: nowrap;
  text-align: right;
  overflow: hidden;
  border-left: solid 3px transparent;
  max-width: fit-content;
  margin-bottom: 1.5rem;
}

.the-type-writer {
  position: relative;
  height: fit-content;
  flex-direction: column;
  display: flex;
  left: 50%; /* Center horizontally */
  transform: translateX(-50%); /* Center horizontally */
}

@keyframes typeWrite {
  from {
    width: 0%;
  }

  to {
    width: var(--width);
  }
}

@keyframes blink {
  to {
    border-left-color: black;
  }

  from {
    border-left-color: transparent;
  }
}

/* end-typewriter */


.nextBtn {
  /* position: absolute; */
  border: none;
  cursor: pointer;
  height: 3rem;
  font-size: 1.4rem;
  color: #ffffff;
  border-radius: 100px;
  background-color: #ff5d8f;
  min-width: 5rem;
  max-width: 7rem;
  /* left:50%;
  transform: translateX(-50%); */
  margin-inline: auto;
  margin-top: 4rem;
  display: block;
  /* bottom: 2rem; */
  transition: background-color 0.3s linear;
  /* animation: fade 2s ease-in-out; */
}

.nextBtn:hover {
    background-color: #fd8aae;
}

.explain-text {
  font-size: 1.3rem;
  color: rgb(79, 77, 77);
  margin: 0;
  display: inline;
  text-align: center;
}

.headline-text{
    font-size: 2rem;

}

@keyframes fade {
  0% {
    opacity: 0; 
  }
  50% {
    opacity: 0.5; 
  }
  100% {
    opacity: 0;
  }
}

@keyframes fade-in {
  from {
    opacity: 0; /* Start with opacity 0 (fully transparent) */
  }
  to {
    opacity: 1; /* End with opacity 1 (fully opaque) */
  }
}

.the-text {
    font-size: 7rem;
    font-weight: bold;
    text-align: center;
}
.fade-in-out-animation {
    animation: fade 4s linear;
}
.fade-in-animation {
    animation: fade-in 2s linear;
}
.tat-text {
    font-size: 2rem;
    text-align: center;
    margin-top: -7rem;
    }
</style>
