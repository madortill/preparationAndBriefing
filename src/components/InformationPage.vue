<template>
    <div id="information-page">
        <!-- <h4 v-if="showTitle" class="text-side-title">{{ arrayTitle[titleIndex] }}</h4> -->
        <main-self-preparation @move-to-ques="toTheQuestion" @move-to-next="nextSub" v-if="sectionNum === 0"></main-self-preparation>
        <targets @move-to-ques="toTheQuestion" @move-to-next="nextSub" v-if="sectionNum === 1"></targets>
        <!-- <feedback-call v-if="titleIndex === 1" @move-to-next="nextSub"></feedback-call>
        <locating-source v-if="titleIndex === 2" @move-to-next="nextSub"></locating-source>
        <objections-feedback v-if="titleIndex === 3" @move-to-next="nextSub"></objections-feedback> -->

        <!-- <component :is="'subj' + titleIndex"></component> -->

    </div>
</template>

<script>
import MainSelfPreparation from '@/components/MainSelfPreparation.vue'; 
import Targets from './Targets.vue';


export default {
    name: 'information-page',
    components: {
        MainSelfPreparation, 
        Targets,
    },
    props: ["titleIndex", 'sectionNum'],
    data() {
        return {
            showTitle: true,
            arrayTitle: [
                'עקרונות יסוד',
                'שיחת משוב',
                'איתור מקור התופעות',
                'התנגדויות במשוב',
            ]
        };
    },
    methods: {

        toTheQuestion () {
            this.$emit('to-question');
        },

        nextSub(subNum) {
            this.$emit('move-sub', subNum);
        },
        nextSection() {
            this.sectionNum++;
        },
    
    },
}

</script>

<style scoped>
.text-side-title {
    position: absolute;
    right: 2%;
    top: 0;
    font-size: 1.5rem;
}

/* .contBtn {
    background-color: #006998;
    position: absolute;
    color: white;
    border: none;
    cursor: pointer;
    border-radius: 10px;
    cursor: pointer;
    width: 9%;
    height: 6%;
    left: 10%;
    bottom: 13%;
    transition: background-color 0.3s linear;
}

.contBtn:hover {
    background-color: #00A4E6;
}

.prevBtn {
    background-color: #006998;
    position: absolute;
    color: white;
    border: none;
    cursor: pointer;
    border-radius: 5px;
    cursor: pointer;
    width: 9%;
    height: 6%;
    bottom: 13%;
    right: 10%;
    transition: background-color 0.3s linear;
}

.prevBtn:hover {
    background-color: #00A4E6;
} */
</style>
