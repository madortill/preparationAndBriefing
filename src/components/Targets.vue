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

    <!-- Static image -->
     <div class="target-graphics-container">
        <img src="../../src/assets/media/target.png" alt="target" class="target"  @click="showNextTarget"/>
        <!-- the arrows -->
        <img  v-for="(i, index) in 4" :key="index" src="../../src/assets/media/arrowTarget.svg" alt="arrow" class="arrow" :class="['arrow' + index , targetNum >= index ? `shoot${index}`: '' ]"/>
     </div>
   

             <!-- Loop through targetsArray to display targets -->
             <div v-for="(target, index) in targetsArray" :key="index" class="target-container" :class="targetNum >= index ?  'target' + index : ''" >
            <p class="text">{{ target }}</p>
        </div>
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
    height: 90rem;
    display: flex;
    flex-direction: column;
    align-items: center;
}
.div-text {
    text-align: center;
    height: 13rem;
}
.title-text {
    margin: auto;
    font-size: 3rem;
    padding-top: 2%;
}

.info-text {
    font-size: 1.7rem;
    color: #3a3737;
    margin-bottom: 0%;
}

.comment-text {
    font-size: 1.3rem;
    margin-top: 0.6%;
}

.target {
    /* position: absolute;
    left: 50%;
    transform: translateX(-50%);
    top: 45%; */
    width: 15rem;
    height: 15rem;
    cursor: pointer;
    grid-row: 1/1;
    grid-column: 1/1;
}

.target-container {
    width: 17rem;
    height: 9rem;
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
    font-size: 1.3rem;
    width: 10rem;
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
    width: 12rem;
    /* position: absolute; */
    /* top: 32rem; */
    z-index: 3;
    pointer-events: none;
    grid-row: 1/1;
    grid-column: 1/1;
    position: relative;
    top: 11.5rem;
    /* left: 40%;
    transform: rotate(10deg); */
}

.arrow0 {
    left: -3rem;
    transform: skew(-10deg);
}
.arrow1 {
    left: 0rem;
    transform: skew(-5deg);
}
.arrow2 {
    left: 3rem;
    transform: skew(5deg);
}
.arrow3 {
    left: 6rem;
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
  
    to {
        top: 5rem;
    }
} 

@keyframes shoot1 {
    to {
        top: 0rem;
    }
}

@keyframes shoot2 {
    to {
        top: 3rem;
    }  
}


@keyframes shoot3 {
    to {
        top: 1rem;
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
  animation: borderPulse 4000ms infinite ease-out;
}

.nextBtn:hover,
.nextBtn:focus {
  animation: borderPulse 4000ms infinite ease-out, hoverShine 200ms;
}
@keyframes borderPulse {
  0% {
    box-shadow: inset 0px 0px 0px 5px rgba(255, 255, 255, 0.4),
      0px 0px 0px 0px rgba(255, 255, 255, 1);
  }
  35% {
    box-shadow: inset 0px 0px 0px 3px rgba(117, 117, 255, 0.2),
      0px 0px 0px 10px rgba(255, 255, 255, 0);
  }
  50% {
    box-shadow: inset 0px 0px 0px 5px rgba(255, 255, 255, 0.4),
      0px 0px 0px 0px rgba(255, 255, 255, 1);
  }
  75% {
    box-shadow: inset 0px 0px 0px 3px rgba(117, 117, 255, 0.2),
      0px 0px 0px 10px rgba(255, 255, 255, 0);
  }
  100% {
    box-shadow: inset 0px 0px 0px 5px rgba(255, 255, 255, 0.4),
      0px 0px 0px 0px rgba(255, 255, 255, 1);
  }
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


.target-graphics-container {
    display: grid;
    grid-template-columns: 1fr; 
    grid-template-rows: 1fr;
    overflow: visible;
}
</style>
