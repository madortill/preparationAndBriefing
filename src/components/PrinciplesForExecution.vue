<template>
    <div id="principle-for-execution">
               <!-- Title and information -->
               <div class="div-text">
            <h2 class="title-text">עקרונות לביצוע</h2>
            <!-- <p class="info-text">
                לתדריך קיימות מספר מטרות:
            </p> -->
          
        </div>

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
            this.$emit("move-to-next", 4);
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
</style>