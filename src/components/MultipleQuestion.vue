<template>
    <div id="multiple-question">
        <div class="answers-container" @click="checkAnswer">
            <h1 class="title-questionMultiple">{{ this.questionInfo.title }}</h1>
            <div class = "div-mulQ">
                <div class="row">
                    <button id="1" ref="1" class="pulse-button-hover">{{ this.questionInfo.ans1
                    }}</button>
                    <button id="2" ref="2" class="pulse-button-hover">{{ this.questionInfo.ans2
                    }}</button>
                     <button id="3" ref="3" class="pulse-button-hover">{{ this.questionInfo.ans3
                    }}</button>
                </div>
                <div class="row">
                    <button id="4" ref="4" class="pulse-button-hover">{{ this.questionInfo.ans4
                    }}</button>
                     <button id="5" ref="5" class="pulse-button-hover">{{ this.questionInfo.ans5
                    }}</button>
                    <button id="6" ref="6" class="pulse-button-hover">{{ this.questionInfo.ans6
                    }}</button>
                </div>
            </div>
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
      };
    },
    methods: {
        checkAnswer(event) {
            if (event.target.classList.contains('pulse-button-hover')) {
                if ( this.isInTheArray(this.questionInfo.correctAnswer, event.target.id)) {
                    event.target.classList.add("correct");
                    if(this.getNumCorrect() === 3) {
                        setTimeout(() => {
                            for (let i = 1; i <= 6; i++) {
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
        }
    },
}
</script>

<style>
#multiple-question {
    display: flex;
    flex-direction: column;
    align-items: center;
}


.answers-container {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.row {
    display: flex;
    margin:  5% 0% 5% 0%;
    justify-content: space-between;
}

.title-questionMultiple {
    color: #5f5a5a;
    font-size: 2.5rem;
    padding: 8% 15%;
    text-align: center;
    margin: 0;
}

.pulse-button-hover {
    background-color: #ff87ab;
    margin: 0 1rem;
    cursor: pointer;
    border: none;
    width: 40%;
    font-size: 1.7rem;
    color: #ffffff;
    border-radius: 100px;
    padding: 20px 30px;
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
    width: 45%;
    height: 40%;
    background: #fff;
    border-radius: 3rem;
    box-shadow: 0 15px 20px -20px rgba(0, 0, 0, 0.4);
    text-align: center;

    /* New styles for centering */
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
</style>
