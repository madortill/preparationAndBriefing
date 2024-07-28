<template>
    <div id="information-page">
        <!-- <h4 v-if="showTitle" class="text-side-title">{{ arrayTitle[titleIndex] }}</h4> -->
        <main-self-preparation @move-to-ques="toTheQuestion" @move-to-next="setSubjNavbar" v-if="sectionNum === 0"></main-self-preparation>
        <targets @show-next="showNextButton" @move-to-ques="toTheQuestion" @move-to-next="nextSub" v-if="sectionNum === 1"></targets>
        <principle-structure @move-to-next="nextSub" v-if="sectionNum === 2"></principle-structure>
        <principles-for-execution @move-to-next="nextSub" v-if="sectionNum === 3"></principles-for-execution>
        <highlights @move-to-next="nextSub" v-if="sectionNum === 4"></highlights>
      
        <button v-if="sectionNum > 0 && showNextBtn"
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

        <!-- <component :is="'subj' + titleIndex"></component> -->

    </div>
</template>

<script>
import MainSelfPreparation from '@/components/MainSelfPreparation.vue'; 
import Targets from './Targets.vue';
import PrincipleStructure from './PrincipleStructure.vue';
import PrinciplesForExecution from './PrinciplesForExecution.vue';
import Highlights from './Highlights.vue';


export default {
    name: 'information-page',
    components: {
        MainSelfPreparation, 
        Targets,
        PrincipleStructure,
        PrinciplesForExecution,
        Highlights,
    },
    props: ["titleIndex", 'sectionNum'],
    data() {
        return {
            showTitle: true,
            arrayTitle: [
                'עקרונות יסוד',
                'שיחת משוב',
                'איתור מקור התופעות',
                'התנגדויות במשוב',
            ],
            showPrevBtn: false,
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
            this.$emit('next-sub');
        },

        lastSub() {
            this.$emit('prev-sub');
        },
        // nextSection(subNum) {
        //     this.sectionNum++;
        //     this.nextSub(subNum);
        // },
        showNextButton() {
            this.showNextBtn = true;
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
  transition: background-color 0.3s linear;
  /* animation: fade 2s ease-in-out; */
}

.nextBtn:hover {
    background-color: #fd8aae;
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
