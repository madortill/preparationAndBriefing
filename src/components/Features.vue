<template>
  <div id="features">
    <img
      v-if="showPart === 0"
      @click.once="toTheQuestions"
      src="@/assets/media/questionMark.png"
      alt="question-mark"
      class="question-mark"
    />
    <div v-if="showPart === 1">
      <ul class="ul-questions">
        <li
          v-for="(item, index) in correctArray"
          :key="index"
          class="list-text"
          :style="`--hue: ${index * 14 + -35}deg`"
        >
          {{ item }}
        </li>
      </ul>

     
    </div>
    <button
     v-if="showPart === 1 "
      class="prevBtn"
      @click="back"
    >
      חזור
    </button>
  </div>
</template>

<script>
export default {
  name: "features",
  components: {},
  data() {
    return {
      page: 0,
      showAbout: false,
      clickBtn: 0,
      showPart: 0,
      correctArray: [
        "מה הוא יודע/לא יודע?",
        "מה אנחנו רוצים שישיג מביצוע זה?",
        "האם ידוע על מאפיינים אישיים של הנחנך שעלולים להשפיע?",
        "מהם התנאים שיבטיחו את הצלחתו/למידתו?",
      ],
    };
  },
  methods: {
    toTheQuestions() {
      this.showPart++;
      this.$emit("next-info");
    }, 
    back() {
      this.showPart--;
      this.$emit('prev-info');
    }
  },
};
</script>

<style scoped>
#features {
  width: 100vw;
  height: 100vh;
}
.question-mark {
  height: 57%;
  position: absolute;
  top: 30%;
  left: 16%;
  animation: bounce 2s linear infinite;
  cursor: pointer;
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

.list-text {
  font-size: 1.5rem;
  list-style: none;
  padding: 20px 35px;
  margin: 15px;
  transition: background-color 0.5s ease;
  background-color: hsl(var(--hue), 70%, 70%);
  border-radius: 15px;
  color: rgb(255, 255, 255);
  text-align: center;

}

.list-text:hover {
    /* cursor: pointer; */
    background-color: hsl(var(--hue), 75%, 83%);

    color: rgb(0, 0, 0);
}

.ul-questions {
    position: absolute;
    top: 35%;
    left: 50%;
    transform: translateX(-50%);
    padding: 0%;
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
