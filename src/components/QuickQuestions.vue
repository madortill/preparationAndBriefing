<template>
    <div id="quick-questions">
      <multiple-question v-if="questionToPass.Qtype === 0 || questionToPass.Qtype === 1" @next-question="updateIndex"
        :questionInfo="questionToPass" :numQues="indexQuestion"></multiple-question>
        <dragging-question v-if="questionToPass.Qtype === 2" :key="questionToPass" @next-question="updateIndex"
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
                }, 
            ],
            // questions2: [
            //     {
            //         Qtype: 0,
            //         title: "מפקד אשר מאמין כי שמירה על קשר עין חשובה יותר מהגעה לשיעור עם בקיאות מלאה בתוכן, ככל הנראה קיימת אצלו בעיה באחד המוקדים. באיזה מוקד מדובר?",
            //         ans1: "תפיסה",
            //         ans2: "מודעות",
            //         ans3: "יישום",
            //         ans4: "למידה",
            //         correctAnswer: 1,
            //         numAnswer: 4,
            //     },
            //     {
            //         Qtype: 2,
            //         title: "סדר/י 3 שאלות למוקד המודעות.",
            //         QArray: [
            //             "חשת ש...?",
            //             "ציינת ש..?",
            //             "ראית ש...?",
            //             "הרגשת ש...?",
            //             "חשבת ש...",
            //             "רצית ש...",
            //             "הסברת ש...",
            //             "שמעת ש...?",
            //         ],
            //         correctArray: [
            //             "ראית ש...?",
            //             "הרגשת ש...?",
            //             "שמעת ש...?",
            //         ]
            //     },
            // ],

            // questions3: [
            //     {
            //         Qtype: 0,
            //         title: "במהלך משוב שמת לב כי המפקד שמולך נמרח על הכיסא ולא מרוכז. כיצד תמשיך/י את שיחת המשוב?",
            //         ans1: "שאילת שאלות",
            //         ans2: "עצירה ושיקוף",
            //         ans3: "להמשיך כרגיל",
            //         ans4: "תדווח למפקד שלו",
            //         correctAnswer: 2,
            //     }, {
            //         Qtype: 0,
            //         title: "נחנך שבשיחת המשוב החל לזרוק לעברך ביטויים עוקצניים ומזלזלים, נחשב לאיזה סוג של מתנגד?",
            //         ans1: "הווכחן",
            //         ans2: "הטראגי",
            //         ans3: "היהיר",
            //         ans4: "המסכים לכאורה",
            //         correctAnswer: 3,
            //     }, {
            //         Qtype: 0,
            //         title: "במידה ובמהלך התמודדות עם התנגדויות שיקפת ושאלת שאלות כלליות והתנהגות הנחנך לא השתנתה, כיצד תמשיך/י את ההתמודדות?",
            //         ans1: "ויכוח עם הנחנך",
            //         ans2: "שאילת שאלות ספציפיות",
            //         ans3: "שיקוף",
            //         ans4: "עצירת המשוב",
            //         correctAnswer: 4,
            //     },
            // ]
        };
    },
    methods: {
        updateIndex() {
            // if (this.indexQ < this[`questions${this.indexQuestion}`].length - 1) {
            //     this.indexQ++;
            // } else {
            //     this.indexQ = 0;
            if(this.indexQ === 0) {
                this.$emit('next-sub');

            }
            // }
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
