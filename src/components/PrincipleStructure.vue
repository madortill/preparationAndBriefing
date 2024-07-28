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
        nextPage() {
            //change the parameter!!!!!!!!!
            this.$emit("move-to-next", 3);
        }
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
</style>