<template>
    <div id="information-page">
        <!-- <h4 v-if="showTitle" class="text-side-title">{{ arrayTitle[titleIndex] }}</h4> -->
        <main-self-preparation @done-info-part-one="doneInfoSubjOne" @move-to-ques="toTheQuestion" @move-to-next="setSubjNavbar" v-if="sectionNum === 0"></main-self-preparation>
        <targets @show-next="showNextButton" @move-to-next="nextSub" v-if="sectionNum === 1"></targets>
        <principle-structure @move-to-next="nextSub" v-if="sectionNum === 2"></principle-structure>
        <!-- <principles-for-execution @move-to-next="nextSub" v-if="sectionNum === 3"></principles-for-execution> -->
        <highlights  @move-to-ques="toTheQuestion" @move-to-next="nextSub" v-if="sectionNum === 3"></highlights>
      
        <button v-if="sectionNum > 0 && showNextBtn || sectionNum > 0 && showBtn"
      class="nextBtn"
      @click="nextSub"
    >
      הבא
    </button>
    <button
     v-if="sectionNum > 1 "
      class="prevBtn"
      @click="lastSub"
    >
      חזור
    </button>

    </div>
</template>

<script>
import MainSelfPreparation from '@/components/MainSelfPreparation.vue'; 
import Targets from './Targets.vue';
import PrincipleStructure from './PrincipleStructure.vue';
import Highlights from './Highlights.vue';


export default {
    name: 'information-page',
    components: {
        MainSelfPreparation, 
        Targets,
        PrincipleStructure,
        Highlights,
    },
    props: ["titleIndex", 'sectionNum', 'showBtn'],
    data() {
        return {
            showTitle: true,
            arrayTitle: [
                'עקרונות יסוד',
                'שיחת משוב',
                'איתור מקור התופעות',
                'התנגדויות במשוב',
            ],
            showNextBtn: false,
        };
    },
    methods: {
        setSubjNavbar(index) {
            this.$emit('set-subj-navbar', index);
        },
        toTheQuestion () {
            this.$emit('to-question');
        },

        nextSub() {
            if(this.sectionNum === 3) {
                console.log('hi');
                this.toTheQuestion();
            } else {
                this.$emit('next-sub');
            }
        },

        lastSub() {
            this.$emit('prev-sub');
        },
        showNextButton() {
            let timer = setTimeout(()=> {
                this.showNextBtn = true;
                clearTimeout(timer);
            }, 900);
        },
        doneInfoSubjOne() {
            this.$emit('done-info-subj-one');
        }
    },
}

</script>

<style scoped>
.text-side-title {
    position: absolute;
    right: 2%;
    top: 0;
    font-size: 1.5rem;
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
  background-color: #ff5d8f;  min-width: 10%;
  max-width: 15%;
  bottom: 10%;
  right: 7%;
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


</style>
