<template>
    <div id="targets">
        <!-- Title and information -->
        <div class="div-text">
            <h2 class="title-text">מטרות</h2>
            <p class="info-text">
                לתדריך קיימות מספר מטרות:
            </p>
            <p class="info-text comment-text">
                - לחצ/י על המטרה -
            </p>
        </div>

        <!-- Loop through targetsArray to display targets -->
        <div v-for="(target, index) in targetsArray" :key="index" class="target-container" :class="targetNum >= index ?  'target' + index : ''" >
            <p class="text">{{ target }}</p>
        </div>

        <!-- the arrows -->
        <!-- <img  v-for="(i, index) in 4" :key="index" src="../../src/assets/media/arrowTarget.svg" alt="arrow" class="arrow" :class="'arrow' + index" :style="targetNum >= index ? 'animation: shoot1 2s ease-in-out forwards' : '' "/> -->

        <img  v-for="(i, index) in 4" :key="index" src="../../src/assets/media/arrowTarget.svg" alt="arrow" class="arrow" :class="['arrow' + index , targetNum >= index ? `shoot${index}`: '' ]"/>

        <!-- Static image -->
        <img src="../../src/assets/media/target.png" alt="target" class="target"  @click="showNextTarget"/>

        <!-- <button
      v-if="targetNum >= 3"
      class="nextBtn"
      @click="nextPage"
    >
      הבא
    </button> -->
    </div>
</template>

<script>
export default {
    name: 'Targets',
    data() {
        return {
            targetsArray: [
                'הקטנת אי ודאות אצל הנחנך',
                'יצירת הבנה ותמונה שלמה',
                'הגדלת סיכויי הצלחת החניך',
                'כלי לשיפור העברת הלמידה'
            ],
            targetNum: -1,
        };
    },
    methods: {
        showNextTarget() {
            this.targetNum++;
            if(this.targetNum >= 3) {
                this.$emit('show-next');
            }
        },
        nextPage() {
            //change the parameter!!!!!!!!!
            this.$emit("move-to-next", 1);
        }
    }
}
</script>

<style scoped>
#targets {
    width: 100vw;
    height: 100vh;
}
.div-text {
    text-align: center;
}

.title-text {
    margin: auto;
    font-size: 3rem;
    padding-top: 2%;
}

.info-text {
    font-size: 1.9rem;
    color: #3a3737;
    margin-bottom: 0%;
}

.comment-text {
    font-size: 1.3rem;
    margin-top: 0.6%;
}

.target {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    top: 45%;
    width: 20rem;
    cursor: pointer;
}

.target-container {
    width: 20rem;
    height: 10rem;
    border-radius: 40px;
    background-color: white;
    text-align: center;
    color: black;
    position: absolute;
    box-shadow: 0 15px 20px -20px rgba(0, 0, 0, 0.4);
    animation: fade 2s ease-in-out;
    display: none;
}

.text {
    color: black;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    margin: 0;
    font-size: 1.5rem;
}

.target0 {
    left: 13%;
    bottom: 48%;
    display: block;
}

.target2 {
    right: 13%;
    bottom: 48%;
    display: block;
}

.target1 {
    left: 13%;
    bottom: 20%;
    display: block;

}

.target3 {
    right: 13%;
    bottom: 20%;
    display: block;
}

@keyframes fade {
  from {
    opacity: 0; /* Start with opacity 0 (fully transparent) */
  }
  to {
    opacity: 1; /* End with opacity 1 (fully opaque) */
  }
}

.arrow {
    width: 15rem;
    position: absolute;
    bottom: -10%;
    z-index: 3;
    pointer-events: none;
    /* left: 40%;
    transform: rotate(10deg); */
}

.arrow0 {
    left: 39%;
    transform: skew(-10deg);
}
.arrow1 {
    left: 44%;
    transform: skew(-5deg);
}
.arrow2 {
    left: 49%;
    transform: skew(5deg);
}
.arrow3 {
    left: 54%;
    transform: skew(10deg);
}
.shoot0 {
    animation: shoot0 0.7s ease-in-out forwards;
}

.shoot1 {
    animation: shoot1 0.7s ease-in-out forwards;
} 

.shoot2 {
    animation: shoot2 0.7s ease-in-out forwards;
}

.shoot3 {
    animation: shoot3 0.7s ease-in-out forwards;
}
@keyframes shoot0 {
    from {
        bottom: -10%;
    }
    to {
        bottom: 10%;
    }
} 

@keyframes shoot1 {
    from {
        bottom: -10%;
    }
    to {
        bottom: 5%;
    }
}

@keyframes shoot2 {
    from {
        bottom: -10%;
    }
    to {
        bottom: 15%;
    }  
}


@keyframes shoot3 {
    from {
        bottom: -10%;
    }
    to {
        bottom: 12%;
    }  
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

</style>
