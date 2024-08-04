<template>
    <div id="principle-structure">
               <!-- Title and information -->
               <div class="div-text">
            <h2 class="title-text">מבנה עקרוני</h2>
            <!-- <p class="info-text">
                לתדריך קיימות מספר מטרות:
            </p> -->
          
        </div>


    </div>

</template>

<script>
export default {
    name: 'principle-structure',
    data() {
        return {
            
        };
    },
    methods: {
       
    }
}
</script>

<style scoped>
#principle-structure {
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