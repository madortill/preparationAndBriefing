<template>
    <div id="targets">
        <!-- the title and info -->
    <div class="div-text">
      <h2 class="title-text">מטרות</h2>
      <p class="info-text">
        לתדריך קיימות מספר מטרות:
      </p>
      <p class="info-text comment-text">
        - לחצ/י על המסך -
    </p>
    </div>

    <div v-for="target in targetsArray" :key="target" class="target-container">
        <p class="text">{{ targetsArray[target] }}</p>
        
    </div>


    <img src="../../src/assets/media/target.png" alt="target" class="target"/>
    </div>
</template>

<script>

export default {
    name: 'targets',
    props: [],
    components: {
        
    },
    data() {
        return {
            targetsArray: ['הקטנת אי ודאות אצל הנחנך', 'יצירת הבנה ותמונה שלמה', 'הגדלת סיכויי הצלחת החניך', 'כלי לשיפור העברת הלמידה'],
        };
    },
    methods: {
      
    },
 
}
</script>

<style scoped>
.div-text {

  text-align: center;
}

.title-text {
  margin: auto;
  font-size: 3rem;
  padding-top: 2%;
}

.info-text {
  position: relative;
  /* padding: 0% 20% 0 35%; */
  /* right: 8%; */
  font-size: 1.9rem;
  display: block;
  z-index: 1;
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
}

.target-container {
    width: 20rem;
    height: 10rem;
    border-radius: 40px;
    background-color: white;
    text-align: center;
    color: black;
}

.text {
    color: black;
    position: absolute;
    top:50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
</style>