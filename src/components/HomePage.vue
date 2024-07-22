<template>
  <div id="home-page">
    <white-window :subjNum="subjNum" @hideWW="hidwWhiteWindow" v-if="showWhiteWindow"></white-window>
    <div v-if="!showWhiteWindow">
      <div v-if="!showQuestions">
        <navbar v-if="showNav" :titleIndex="subIndex"></navbar>
        <information-page
          :titleIndex="titleIndex"
          @move-sub="moveSub"
          @close-nav="closeNav"
          @to-question="showQuestion"
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
      index: 0,
      titleIndex: 0,
      showNav: true,
      showQuestions: false,
      indexQuestion: 0,
      subIndex: -1,
      subjNum: 0,
    };
  },

  methods: {
    hidwWhiteWindow() {
      this.showWhiteWindow = false;
    },
    nextSub() {
      this.showQuestions = false;
      this.showWhiteWindow = true;
      this.subjNum++;
      // if (this.titleIndex === 5) {
      //   this.$emit("next-page");
      // }
    },
    showQuestion() {
      this.showQuestions = true;
    },
    moveSub(subNum) {
      this.subIndex = Number(subNum);
      // console.log(showQ);
      // this.showQuestions = false;

      // if (showQ === true) {
      //   this.showQuestions = true;
      //   this.indexQuestion++;
      // } else {
      //   this.showQuestions = false;
      // }

      // if (this.titleIndex >= 0 && this.titleIndex <= 4) {
      //   this.titleIndex++;
      // }
    },
    closeNav() {
      this.showNav = false;
    },
  },
};
</script>

<style>
#home-page {
  background-color: #f2f2f2;
  width: 100vw;
  height: 100vh;
  /* display: flex; */
  position: absolute;
  justify-content: center;
}
</style>
