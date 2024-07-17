<template>
    <div id="mission-planning">
     <!-- flipcards -->
     <div class="flip-card-container">
            <div v-for="( item, index) in arrayFront" :key="index" :class="['flip-card', this.onStart]">
                <div class="flip-card-inner" :style="`--hue: ${index * 8 + 690}deg`">
                    <div class="flip-card-front">
                        <img :src="src(item)" class="imgFront">
                    </div>
                    <div class="flip-card-back">
                        <h1 class="textBack">{{ arrayBack[index] }} </h1>
                    </div>
                </div>
            </div>
        </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "mission-planning",
    components: {},
    data() {
      return {
        page: 0,
         onStart: 'start',
        clickBtn: 0,
        showPart: 0,
        arrayBack: [
          "איסוף מידע",
          "הכנות לוגיסטיות סופיות",
          "הגדרת מטרות וזמן למשימה",
          "הכנת הנחיות והוראות בטיחות"
        ],
        arrayFront: [
            "symbol1.png", "symbol2.png",
            "symbol3.svg",
            "symbol4.svg"
        ]
      };
    },
    mounted() {
       
                setTimeout(() => {
                    this.onStart = 'off';
                }, 100);
           
    },
    methods: {
        src(name) {
            return new URL(`../assets/media/flipCard/${name}`, import.meta.url).href
        },
    },
  };
  </script>
  
  <style>
  #mission-planning {
    width: 100vw;
    height: 100vh;
  }

  .flip-card-container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    height: 50%;
    width:100%;
    bottom: 20%;
}

.flip-card {
    background-color: transparent;
    width: 300px;
    height: 300px;
    perspective: 1000px;
    margin: 10px;
}

.flip-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    text-align: center;
}

.flip-card:hover .flip-card-front, .flip-card.start .flip-card-front{
    transform: rotateY(180deg);
}

.flip-card:hover .flip-card-back, .flip-card.start .flip-card-back{
    transform: rotateY(360deg)
}

.flip-card-front,
.flip-card-back {
    transition: transform 0.6s;
    transform-style: preserve-3d;
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
}

.flip-card-front {
    background-color: hsl(var(--hue), 90%, 75%);
    border-radius: 30px;
    color: black;
    /* cursor: pointer; */
}

.flip-card-back {
    background-color: hsl(var(--hue), 90%, 90%);
    border-radius: 30px;
    color: rgb(84, 82, 82);
    transform: rotateY(180deg);
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
    /* cursor: pointer; */
}

.imgFront {
    width: 60%;
    position: absolute;
    left: 20%;
    top: 20%;
}

.over-me {
    position: absolute;
    top: 70%;
    right: 10%;
    font-size: 1.2rem;
    color: #5f5a5a;
    /* animation: floatAnimation 3s ease-in-out infinite; */
}

.textBack {
    padding: 5%;
}
  
  </style>
  