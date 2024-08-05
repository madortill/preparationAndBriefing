<template>
  <div id="main-self-preparation">
    <!-- the title and info -->
    <div v-if="showAnimation" class="div-text fade-in">
      <h2 class="title-text">{{ arrayTitle[indexTitle] }}</h2>
      <p :class="indexInfo === 3 ? 'features-text' : 'info-text'">
        {{ arrayInfo[indexInfo] }}
      </p>
      <p class="info-text" v-show="indexInfo === 5">
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
    <features @next-info="nextInfo" @prev-info="prevInfo" v-if="indexTitle === 2"></features>
    <mission-planning v-if="indexTitle === 1"></mission-planning>

    <button
      v-if="
        ((indexTitle === 0 && counter === 3) || indexTitle !== 0) &&
        indexInfo !== 3
      "
      class="nextBtn"
      @click="backToMain"
    >
      {{ nextBtnText }}
    </button>
    <button
    v-if="showPrevBtn"
      class="prevBtn"
      @click="backToFirstLF"
    >
      חזור
    </button>
  </div>
</template>

<script>
import Features from "./Features.vue";
import MissionPlanning from "./MissionPlanning.vue";
export default {
  name: "main-self-preparation",
  components: { Features, MissionPlanning },
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
        "במהלך התכנון עלינו לבצע מספר פעולות:",
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
      ableBtns: false,
      chosenSub: -1,
      nextBtnText: "המשך",
      showPrevBtn: false,
    };
  },
  mounted() {
    // Call a method to change data after 3 seconds
    setTimeout(this.setStartAnimation, 2500);
  },
  methods: {
    circleBtn(event) {
      if (this.ableBtns) {
        this.chosenSub = event.currentTarget.id;
        this.indexTitle = Number(this.chosenSub) + 1;

        //flips
        if (this.chosenSub === "2") {
          this.chosenSub = 0;
          this.indexInfo = this.arrayInfo.length - 1;
        } else if (this.chosenSub === "1") {
          this.chosenSub = 1;
          this.indexInfo = 3;
        } else if (this.chosenSub === "0") {
          this.chosenSub = 2;
          this.indexInfo = 1;
        }

        this.$emit("move-to-next", this.chosenSub);
      }
    },
    setStartAnimation() {
      this.showAnimation = true;
      setTimeout(() => {
        this.ableBtns = true;
      }, 1000);
    },

    backToMain() {
      if (this.indexTitle === 0) {
        this.$emit("move-to-ques");
      } else {
        //cheking if user entered before
        if (!this.arrayDoneSubj[this.indexTitle - 1]) {
          this.arrayDoneSubj[this.indexTitle - 1] = true;
          this.counter++;
          if (this.counter === 3) {
            this.nextBtnText = "הבא";
            this.$emit('done-info-part-one');
          }
        }
        this.indexTitle = 0;
        this.indexInfo = 0;
        this.$emit("move-to-next", -1);
      }
    },

    nextInfo() {
      this.indexInfo--;
    },
    prevInfo() {
      this.indexInfo++;
    }
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
  font-size: 1.5rem;
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
  font-size: 2.5rem;
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
  bottom: 10%;
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
.prevBtn:hover {
  animation: borderPulse 4000ms infinite ease-out, hoverShine 200ms;
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
  width: 15rem;
  height: 5rem;
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
  width: 15rem;
  height: 15rem;
  padding: 2%;
  cursor: pointer;
}

.circle-ago {
  z-index: 0;
  width: 14rem;
  height: 14rem;
  border-radius: 50%;
  text-align: center;
  color: rgb(65, 63, 63);
  font-size: 1.7rem;
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
  bottom: 20%;
}

.circle-ago:nth-child(2) {
  bottom: 20%;
}

.circle-ago:nth-child(3) {
  right: 20%;
  bottom: 20%;
}

.floatAnimation {
  animation: floatAnimation 2s linear infinite;
}

.downAndGrow {
  animation: downAndGrow 2.5s ease-in-out;
}

@keyframes downAndGrow {
  0% {
    font-size: 0rem;
    width: 1rem;
    height: 1rem;
    bottom: 87%;
  }

  100% {
    font-size: 1.7rem;
    width: 14rem;
    height: 14rem;
    bottom: 20%;
  }
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

.disabled {
  background-color: #dcdcdc;
}

.prevBtn {
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
  bottom: 10%;
  animation: fade 2s ease-in-out;
   
    right: 10%;
    transition: background-color 0.3s linear;
}

.prevBtn:hover {
    background-color: #fd8aae;
} 
</style>
