<template>
  <div id="highlights">
    <!-- Title and information -->
    <div class="div-text">
      <h2 class="title-text">דגשים לתדריך</h2>
      <p class="info-text">
        על מנת לבצע תדריך אפקטיבי, יש להקפיד על הדגשים הבאים:
      </p>
    </div>
<!-- the list -->
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
</template>

<script>
export default {
  name: "highlights",
  components: {},
  data() {
    return {
      correctArray: [
        "אין ללמד חומר חדש",
        "תדריך לימודי אינו הרצאה!",
        "תדריך קבוצתי ילווה בתדריך אישי",
        "עמידה בזמנים - קצר ולעניין",
      ],
    };
  },
  methods: {
 
  },
};
</script>

<style scoped>

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
width: 40%;
position:relative;
right:26%;
}

.list-text:hover {
    /* cursor: pointer; */
    background-color: hsl(var(--hue), 75%, 83%);

    color: rgb(0, 0, 0);
}

.div-text {
  width: 100%;
  height: 60%;
  text-align: center;
}

.title-text {
  margin: auto;
  font-size: 3rem;
  padding-top: 2%;
}

.info-text {
  position: relative;
  padding: 0% 20% 0 35%;
  right: 8%;
  font-size: 1.9rem;
  display: block;
  z-index: 1;
  color: #3a3737;
}
</style>
