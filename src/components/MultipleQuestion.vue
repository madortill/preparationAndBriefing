<template>
    <div id="multiple-question">
        <div class="answers-container" @click="checkAnswer">
            <h1  v-if="part !== 0 || this.questionInfo.Qtype !== 1" class="title-questionMultiple">{{ this.questionInfo.title }}</h1>
            <h2 v-if="this.questionInfo.Qtype === 0" class="second-instraction">בחר/י בשלוש התשובות הנכונות.</h2>
            <h1 class="title-questionMultiple" v-if="this.questionInfo.Qtype === 1  && part === 0">לפניכם ביצוע תדריך שגוי.</h1>
            <div class = "div-mulQ">
                <!-- Qtype =  0 -->
                <div class="row" v-if="this.questionInfo.Qtype === 0">
                    <!-- <button v-for="i in 3" :key="i" :id="i" :ref="`button${i}`" class="pulse-button-hover"> {{ questionInfo['ans' + i] }}</button> -->

                    <button id="1" ref="1" class="pulse-button-hover">{{ this.questionInfo.ans1
                    }}</button>
                    <button id="2" ref="2" class="pulse-button-hover">{{ this.questionInfo.ans2
                    }}</button>
                     <button id="3" ref="3" class="pulse-button-hover">{{ this.questionInfo.ans3
                    }}</button>
                </div>
                <div class="row" v-if="this.questionInfo.Qtype === 0">
                    <button id="4" ref="4" class="pulse-button-hover">{{ this.questionInfo.ans4
                    }}</button>
                     <button id="5" ref="5" class="pulse-button-hover">{{ this.questionInfo.ans5
                    }}</button>
                    <button id="6" ref="6" class="pulse-button-hover">{{ this.questionInfo.ans6
                    }}</button>
                </div>
                <!-- Qtype =  1 -->
                 <div v-if="part === 0 && this.questionInfo.Qtype === 1">
                    <p class="explain-text">הסמלת מיה עשתה תדריך למספר מפק"ציות לקראת המשובים שלהן.
בתחילת התדריך מיה הציגה את מטרות התצפית, עברה על דף התצפית עד הבנה מלאה, נתנה את דגשיה ולאחר מכן שאלה אם יש להן שאלות וסיימה את התדריך.
</p>

                 </div>
                <div class="row" v-if="this.questionInfo.Qtype === 1 && part === 1">
                    <button id="1" ref="1" class="pulse-button-hover">{{ this.questionInfo.ans1
                    }}</button>
                    <button id="2" ref="2" class="pulse-button-hover">{{ this.questionInfo.ans2
                    }}</button>
                   
                </div>
                <div class="row" v-if="this.questionInfo.Qtype === 1  && part === 1">
                    <button id="3" ref="3" class="pulse-button-hover">{{ this.questionInfo.ans3
                    }}</button>
                </div>
            </div>
            <button class="nextBtn" v-if="part === 0  && this.questionInfo.Qtype === 1" @click="nextPart">הבא</button>
            <img @click="backToStory" v-if="part === 1" src="../../src/assets/media/question-mark-reminder.png" alt="reminder" class="reminder"/>
            <p v-if="part === 1" class="reminder-text">לחץ לתזכורת לתדריך</p>

            <button
      class="prevBtn"
      @click="backToInfo"
    >
      חזור
    </button>
        </div>
    </div>
</template>

<script>

export default {
    name: 'multiple-question',
    props: ['questionInfo'],
    data() {
      return {
        arrayChosenCorrect: ['', '', ''],
        part: 0,
      };
    },
    methods: {
        checkAnswer(event) {
            if (event.target.classList.contains('pulse-button-hover')) {
                if ((this.questionInfo.Qtype === 0 && this.isInTheArray(this.questionInfo.correctAnswer, event.target.id)) || (this.questionInfo.Qtype !== 0 &&  String(event.target.id) === String(this.questionInfo.correctAnswer))) {
                    event.target.classList.add("correct");
                    if(this.questionInfo.Qtype === 0 && this.getNumCorrect() === 3 || this.questionInfo.Qtype !== 0 ) {
                        setTimeout(() => {
                            for (let i = 1; i <= this.questionInfo.numAnswer; i++) {
                                if (this.$refs[i].classList.contains('correct')) {
                                    this.$refs[i].classList.remove('correct');
                                }
                                if (this.$refs[i].classList.contains('wrong')) {
                                    this.$refs[i].classList.remove('wrong');
                                }
                            }
                            this.$emit('next-question')
                        }, 1500);
                    }
                       
                } else {
                    event.target.classList.add("wrong");
                }
            }
        },
        isInTheArray (arr, currentId) {
           
            for (let i = 0 ; i < arr.length ; i++) {
                if(String(arr[i]) === String(currentId)) {
                    this.arrayChosenCorrect[i] = true;
                    return true;

                }
            }
            return false;
        },
        getNumCorrect() {
            let counter = 0 ;
            for (let i = 0 ; i < 3 ; i++) {
                if(this.arrayChosenCorrect[i]) {
                    counter++;
                }
            }
            return counter;
        },
        nextPart() {
            this.part++;
            this.$emit('next-part');
        },
        backToStory() {
            this.part--;
            this.$emit('last-part');
        },
        backToInfo() {
            this.$emit('back-to-info');
        }
    },
}
</script>

<style scoped>
#multiple-question {
    display: flex;
    flex-direction: column;
    align-items: center;
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
  animation: fade 2s ease-in-out;
}

.explain-text {
  font-size: 1.5rem;
  color: rgb(79, 77, 77);
  margin: 0;
  display: inline;
  text-align: center;
  position: absolute;
  top:50%;
  left:50%;
  transform: translate(-50%, -50%);
  width:90%
}

.answers-container {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.row {
    display: flex;
    margin:  5% 0% 5% 0%;
    justify-content: center;
}

.title-questionMultiple {
    color: #5f5a5a;
    font-size: 2.2rem;
    /* the rem */
    padding: 8rem 15%;
    text-align: center;
    margin-top: -2rem;
    width: 100%;
}

.pulse-button-hover {
    background-color: #ff87ab;
    margin: auto;
    cursor: pointer;
    border: none;
    width: 11rem;
    height: 6.5rem;
    font-size: 1.4rem;
    color: #ffffff;
    border-radius: 100px;
    padding: 10px 10px;
}

.pulse-button-hover:hover {
    animation: borderPulse 4000ms infinite ease-out, hoverShine 200ms;
}

@keyframes borderPulse {
    0% {
        box-shadow: inset 0px 0px 0px 5px rgba(255, 255, 255, 0.4), 0px 0px 0px 0px rgba(255, 255, 255, 1);
    }

    100% {
        box-shadow: inset 0px 0px 0px 3px rgba(24, 24, 176, 0.2), 0px 0px 0px 10px rgba(255, 255, 255, 0);
    }
}

@keyframes hoverShine {
    0% {
        background-image: linear-gradient(135deg, rgba(255, 255, 255, .4) 0%, rgba(255, 255, 255, 0) 50%, rgba(255, 255, 255, 0) 100%);
    }

    50% {
        background-image: linear-gradient(135deg, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, .4) 50%, rgba(255, 255, 255, 0) 100%);
    }

    100% {
        background-image: linear-gradient(135deg, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, 0) 50%, rgba(255, 255, 255, .4) 100%);
    }
}

.correct {
    background-color: green;
}

.wrong {
    background-color: rgb(176, 6, 6);
}

.disabled {
    background-color: rgb(140, 139, 132);
    color: rgb(196, 194, 177);
    cursor: none;
}
.div-mulQ {
    position: absolute;
    width: 40rem;
    height: 21rem;
    background: #fff;
    border-radius: 3rem;
    box-shadow: 0 15px 20px -20px rgba(0, 0, 0, 0.4);
    text-align: center;

    /* New styles for centering */
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}

.reminder {
    position: absolute;
    top: 8%;
    right: 5rem;
    width: 16rem;
    cursor: pointer;
}

.second-instraction {
    color: #5f5a5a;
    text-align: center;
    margin-top: -10rem;
    width: 100%;
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
  right: 10%;
}

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

.reminder-text {
    position: absolute;
    top: 7.5rem;
    right: 8.5rem;
    color: grey
    }
</style>
