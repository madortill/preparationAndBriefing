<template>
    <div id="quick-questions">
      <multiple-question v-if="questionToPass.Qtype === 0 || questionToPass.Qtype === 1" @next-question="updateIndex"
        :questionInfo="questionToPass" :numQues="indexQuestion"  @next-part="nextPart" @last-part="lastPart"></multiple-question>
        <dragging-question v-if="questionToPass.Qtype === 2" :key="questionToPass" @next-to-end="toTheEnd"
        :questionInfo="questionToPass"></dragging-question>
     
    </div>
  </template>
  

<script>
import DraggingQuestion from './DraggingQuestion.vue';
import MultipleQuestion from "./MultipleQuestion.vue";



export default {
    name: 'quick-questions',
    props: [ 'indexQ'],
    components: {
        MultipleQuestion,
        DraggingQuestion,
    },
    data() {
        return {
            typeQuestion: 0,
            inPart2: false,
            questions: [
                {
                    Qtype: 0,
                    title: "באילו תחומים ניגע בזמן ההכנה עצמית לתדריך?",
                    ans1: "למידת מאפייני הנחנך",
                    ans2: "הכנות לוגיסטיות סופיות",
                    ans3: "קביעת מיקום המתצפת",
                    ans4: "שיחת חולין עם הנחנך",
                    ans5: "סגירה מקצועית של החומר",
                    ans6: "תכנון מתווה המשימה",
                    correctAnswer: [1, 5,6],
                    numAnswer: 6,
                },
                {
                    Qtype: 1,
                    title: "מה חסר בתדריך?",
                    ans1: "לא היה תדריך אישי לאחר קבוצתי",
                    ans2:  "תהליך הצגת המתווה היה שגוי ",
                    ans3:  "הציגה בסדר לא הגיוני",
                    correctAnswer: 1,
                    numAnswer: 3,
                }, {
                    Qtype: 2,
               title: "מהם הדגשים לתדריך?",
                    QArray: [
                        "תדריך לימודי לא הרצאה",
                        "שיחת חולין",
                        "הצגה עצמית",
                        "עמידה בזמנים - קצר ולעניין",
                        "אין ללמד חומר חדש",
                        "וידוא הבנה",
                        "תדריך קבוצתי ילווה בתדריך אישי",
                    ],
                    correctArray: [
                        "תדריך לימודי לא הרצאה",
                        "עמידה בזמנים - קצר ולעניין",
                        "אין ללמד חומר חדש",
                        "תדריך קבוצתי ילווה בתדריך אישי",
                    ]                
                },
            ],
            
        };
    },
    methods: {
        updateIndex() {
            if(this.indexQ === 0) {
                this.$emit('next-sub');

            } else if(this.indexQ === 1 && this.inPart2) {
                this.$emit('to-question');
            }
            // }
        },
        nextPart() {
            this.inPart2 = true;
        },
        lastPart() {
            this.inPart2 = false;
        },
        toTheEnd() {
            this.$emit('to-end-screen');
        }
        
    },
    computed: {
        // questionToPass() {
        //     return (
        //         this[`questions${this.indexQuestion + 1}`][this.indexQ]
        //     )
        // }
        questionToPass() {
            return (
                this[`questions`][this.indexQ]
            )
        }
    }
}
</script>

<style>
#quick-questions {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    /* height: 60vh;  */
}
</style>
