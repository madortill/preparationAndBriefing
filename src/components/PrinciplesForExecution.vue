<template>
    <div id="principle-for-execution">
               <!-- Title and information -->
               <div class="div-text">
            <h2 class="title-text">עקרונות לביצוע</h2>
            <!-- <p class="info-text">
                לתדריך קיימות מספר מטרות:
            </p> -->
            <video width="700" height="490" controls  autoplay>
            <source src="../../src/assets/video/second.mp4" type="video/mp4">
            your browser does not support video tag
          </video>
        </div>

        <button
      class="nextBtn"
      @click="nextPage"
    >
      הבא
    </button>
    </div>

</template>

<script>
export default {
    name: 'principle-for-execution',
    data() {
        return {
            
        };
    },
    methods: {
        nextPage() {
            //change the parameter!!!!!!!!!
            this.$emit("move-to-next", 3);
        }
    }
}
</script>

<style scoped>
#principle-for-execution {
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