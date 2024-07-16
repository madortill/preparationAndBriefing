<template>
  <div id="main-self-preparation">
    <!-- the title and info -->
    <div v-if="showAnimation" class="div-text fade-in">
      <h2 class="title-text">{{ arrayTitle[indexTitle] }}</h2>
      <p :class=" indexInfo === 3 ?'features-text' : 'info-text'">
        {{ arrayInfo[indexInfo] }}
      </p>
      <p class='info-text' v-show="indexInfo === 5">
        {{ arrayInfo[indexInfo - 1] }}
      </p>
    </div>

    <!-- circles section -->
    <div v-show="indexTitle === 0" class="ago-container">
      <div
        v-for="(item, index) in arrayCircle"
        :key="index"
        :id="index"
        class="circle-ago"
        :style="{
          '--hue': `${index * 15 + 315}deg`,
        }"
        :class="[
          showAnimation ? 'floatAnimation' : 'downAndGrow',
          arrayDoneSubj[index] ? 'disabled' : '',
        ]"
        @click="circleBtn"
      >
        {{ arrayCircle[index] }}
      </div>
    </div>

    <!-- the area info -->
    <features @next-info="nextInfo" v-if="indexTitle === 2"></features>

    <button
      v-if="((indexTitle === 0 && counter === 3) || indexTitle !== 0)  && indexInfo !== 3"
      class="nextBtn"
      @click="backToMain"
    >
  {{ nextBtnText }}
    </button>
  </div>
</template>

<script>
import Features from './Features.vue';
export default {
  name: "main-self-preparation",
  components: {Features},
  data() {
    return {
      arrayTitle: [
        "להכנה עצמית שלושה תחומים:",
        "תכנון מתווה המשימה",
        "למידת מאפייני הנחנך",
        '"סגירה" מקצועית של החומר',   
      ],
      arrayInfo: [
        "- לחצ/י על תחום -",
        "התוצר הסופי של שלב ההכנה העצמית",
        "השאלות הן:",
        "על מנת לגשת לתדריך בצורה הטובה ביותר, עלינו לשאול את עצמנו מספר שאלות לגבי הנחנך שלנו.",
        "החונך נדרש לאבחן את אתגרי המשימה איתם נדרש להתמודד הנחנך.",
        "על החונך ללמוד ולהתרענן בנושאים המקצועיים של המשימה.",  
      ],
      arrayCircle: [
        "תכנון מתווה המשימה",
        "למידת מאפייני הנחנך",
        '"סגירה" מקצועית של החומר',
      ],
      arrayDoneSubj: [false, false, false],
      arrayPrinciple: ["תמיכה באגו הנחנך.", "איסוף מקסימום מידע מהנחנך."],
      showQ: false,
      // index: 0,
      subj: 1,
      indexTitle: 0,
      indexInfo: 0,
      showBtnCall: false,
      showMashov: false,
      onStart: "start",
      counter: 0,
      showAnimation: false,
      chosenSub: -1,
      nextBtnText: 'המשך',
    };
  },
  mounted() {
    // Call a method to change data after 3 seconds
    setTimeout(this.setStartAnimation, 3000);
  },
  methods: {
    circleBtn(event) {
      this.chosenSub = event.currentTarget.id;
      this.indexTitle = Number(this.chosenSub) + 1;
      
      //flips
      if(this.chosenSub === '2') {
        this.chosenSub = 0;
      this.indexInfo = this.arrayInfo.length - 1;
      } else if(this.chosenSub === '1') {
        this.chosenSub = 2;
        this.indexInfo = 3;
      } else if(this.chosenSub === '0') {
        this.chosenSub = 2;
        this.indexInfo = 1;
      }

      this.$emit('move-to-next', this.chosenSub);
    },
    setStartAnimation() {
      this.showAnimation = true;
    },

    backToMain() {
      //cheking if user entered before
      if (!this.arrayDoneSubj[this.indexTitle - 1]) {
       
        this.arrayDoneSubj[this.indexTitle - 1] = true;
        this.counter++;
        if (this.counter === 3) {
          this.nextBtnText= 'הבא';
        }
      }
      this.indexTitle = 0;
      this.indexInfo = 0;  
      this.$emit('move-to-next', -1);
    },

    nextInfo() {
      this.indexInfo--;
    },
  },
};
</script>

<style scoped>
@keyframes fade {
  from {
    opacity: 0; /* Start with opacity 0 (fully transparent) */
  }
  to {
    opacity: 1; /* End with opacity 1 (fully opaque) */
  }
}

/* Apply the fade animation to an element */
.fade-in {
  animation: fade 3s ease-in-out; /* Animation name, duration, timing function */
}

.div-text {
  width: 100%;
  height: 60%;
  text-align: center;
}

.info-text {
  position: relative;
  padding: 0% 20% 0 35%;
  right: 8%;
  font-size: 1.9rem;
  display: block;
  z-index: 1;
  color: #3a3737;
}

.features-text {
  position: absolute;
  right: 22%;
  width: 28%;
  top: 45%;
  font-size: 1.8rem;
  color: #3a3737;
}

.info-div-text {
  position: relative;
  padding: 0% 20% 0 35%;
  right: 8%;
  font-size: 2.2rem;
  display: block;
  z-index: 1;
  color: #ffffff;
  margin-top: 4.5%;
}

.title-text {
  margin: auto;
  font-size: 3rem;
  padding-top: 2%;
}

.nextBtn {
  position: absolute;
  border: none;
  cursor: pointer;
  height: 5%;
  font-size: 1.4rem;
  color: #ffffff;
  border-radius: 100px;
  background-color: #ff5d8f;
  min-width: 10%;
  max-width: 15%;
  left: 7%;
  bottom: 13%;
}

.prevBtn {
  position: absolute;
  border: none;
  cursor: pointer;
  height: 5%;
  font-size: 1.6rem;
  color: #ffffff;
  border-radius: 100px;
  background-color: #0492bd;
  min-width: 10%;
  max-width: 15%;
  bottom: 13%;
  right: 8%;
}

.nextBtn:hover,
.prevBtn:hover,
.callBtn:hover {
  animation: borderPulse 4000ms infinite ease-out, hoverShine 200ms;
}

.callBtn {
  position: absolute;
  border: none;
  cursor: pointer;
  border-radius: 100px;
  background-color: #67c6c7;
  color: #ffffff;
  min-width: 15%;
  max-width: 15%;
  height: 13%;
  font-size: 2.5rem;
  left: 50%;
  transform: translateX(-50%);
  top: 70%;
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

.circle {
  width: 18rem;
  height: 7rem;
  border-radius: 100px;
  background-color: #68d8d6;
  text-align: center;
  color: #ffffff;
  font-size: 2rem;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 2%;
  transition: all 0.3s ease;
  position: fixed;
  box-shadow: 0 5px 7px rgba(0, 0, 0, 0.2);
}

.circle:nth-child(1) {
  top: 30%;
  left: 25%;
}

.circle:nth-child(2) {
  top: 30%;
  right: 25%;
}

.circle-ago:hover {
  box-shadow: 0 15px 9px rgba(0, 0, 0, 0.4);
  width: 17rem;
  height: 17rem;
  padding: 2%;
  cursor: pointer;
}

.circle-ago {
  z-index: 0;
  width: 15rem;
  height: 15rem;
  border-radius: 50%;
  text-align: center;
  color: rgb(65, 63, 63);
  font-size: 2rem;
  font-weight: 550;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 1.6%;
  transition: all 0.3s ease;
  box-shadow: 0 5px 7px rgba(0, 0, 0, 0.2);
  background-color: hsl(var(--hue), 63%, 75%);
  position: fixed;
}

.ago-container {
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  padding: 1rem;
}

.circle-ago:nth-child(1) {
  left: 20%;
  bottom: 25%;
}

.circle-ago:nth-child(2) {
  bottom: 25%;
}

.circle-ago:nth-child(3) {
  right: 20%;
  bottom: 25%;
}

.floatAnimation {
  animation: floatAnimation 3s ease-in-out infinite;
}

.downAndGrow {
  animation: downAndGrow 3s ease-in-out;
}

@keyframes downAndGrow {
  0% {
    font-size: 0rem;
    width: 1rem;
    height: 1rem;
    bottom: 87%;
  }

  100% {
    font-size: 2rem;
    width: 15rem;
    height: 15rem;
    bottom: 25%;
  }
}
.disabled {
  background-color: #dcdcdc;
}
</style>
