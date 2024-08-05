<template>
  <div id="home-page">
    <white-window :subjNum="subjNum" @hideWW="hidwWhiteWindow" v-if="showWhiteWindow"></white-window>
    <div v-if="!showWhiteWindow">
      <div v-if="!showQuestions">
        <navbar v-if="showNav" :titleIndex="subIndex" :part="subjNum"></navbar>
        <img v-if="(showNav && subjNum === 1) || (showNav && doneSubj1 && beenInSubj2 && subjNum === 0)" title="החלף נושא" src="../../src/assets/media/replace.svg" class="replace" @click="replaceSubj" alt="replace-icon"/>
        <information-page
          :titleIndex="titleIndex"
          @next-sub="nextMiniSub"
          @prev-sub="prevMiniSub"
          @set-subj-navbar= "setMiniSubInNavbar"
          @close-nav="closeNav"
          @to-question="showQuestion"
          @done-info-subj-one="doneInfoSubjOne"
          :sectionNum="miniSubNum"
          :showBtn="showNextBtn"
        ></information-page>
      </div>
      <div v-if="showQuestions">
        <quick-questions
          :indexQ="indexQuestion"
          @next-sub="nextSub"
          @to-question="showQuestion"
          @to-end-screen="toEndScreen"
          @back-from-ques="backToQues"
        ></quick-questions>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import InformationPage from "./InformationPage.vue";
import QuickQuestions from "./QuickQuestions.vue";
import WhiteWindow from "./WhiteWindow.vue";

export default {
  name: "home-page",
  components: {
    Navbar,
    InformationPage,
    QuickQuestions,
    WhiteWindow,
  },

  data() {
    return {
      showWhiteWindow: true,
      // index: 0,
      titleIndex: 0,
      showNav: true,
      showQuestions: false,
      indexQuestion: -1,
      subIndex: -1,
      subjNum: 0,
      miniSubNum: -1,
      doneSubj1: false,
      beenInSubj2: false,
      showNextBtn: false,
    };
  },

  methods: {
    hidwWhiteWindow(partNum) {
      this.showWhiteWindow = false;
      if(partNum === 5) {
        this.miniSubNum++;
        // this.subIndex = 0;
      }
      
    },
    nextSub() {
      this.showQuestions = false;
      this.showWhiteWindow = true;
      this.subjNum++;
      this.subIndex = 0;
    },
    showQuestion() {
      this.showQuestions = true;
      this.indexQuestion++;
    },
    setMiniSubInNavbar(subNum) {
      this.subIndex = Number(subNum);
    },
    nextMiniSub() {
        this.miniSubNum++;  
     this.subIndex++;
    },
    prevMiniSub() {
      this.miniSubNum--; 
      this.subIndex--;
    },
    closeNav() {
      this.showNav = false;
    },
    toEndScreen() {
      this.$emit('next-page');
    },
    replaceSubj() {
      if(this.subjNum === 1) {
        this.subjNum = 0;
        this.indexQuestion = -1;
        this.miniSubNum = 0;
        this.subIndex = -1;
        this.titleIndex = 0;
        this.beenInSubj2 = true;
      } else if(this.subjNum === 0) {
        this.subjNum = 1;
        this.indexQuestion = 0;
        this.miniSubNum = 1;
        this.subIndex = 0;
        this.titleIndex = 0;
      }
    },
    doneInfoSubjOne() {
      this.doneSubj1 = true;
    },
    backToQues() {
      this.showQuestions = false;
      this.indexQuestion--;
      this.showNextBtn = true;
    }
  },
};
</script>

<style>
#home-page {
  background-color: #f2f2f2;
  width: 100vw;
  height: 100vh;
}

.replace {
  position: absolute;
  right: 14vw;
  top: 2.5rem;
  width: 2.5rem;
  cursor: pointer;
}
</style>
