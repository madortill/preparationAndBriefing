<template>
    <div id="navbar">
      <div class="container">
        <nav>
          <!-- <ul @click="chosenTitle">
                      <li class="subject">{{subjects[part][0]}}</li>
                      <li  v-for="subj in subjects[part] - 1" :key="subj" :class="{ active: titleIndex === subj-1 }">{{subjects[part][subj]}}</li>
                  </ul> -->
  
          <ul @click="chosenTitle">
            <li class="subject">{{ subjects[part][0] }}</li>
            <li
              v-for="(subj, index) in subjects[part].slice(1)"
              :key="index"
              :class="{ active: titleIndex === index }"
              :id="index"
            >
              {{ subj }}
            </li>
          </ul>
          
        </nav>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "navbar",
    props: ["titleIndex", 'part'],
    data() {
      return {
        subjects: [
          ["הכנה עצמית", 'סגירת" החומר"', "מאפייני הנחנך", "תכנון המשימה"],
          ["תדריך", "מטרות", "מבנה עקרוני", "עקרונות לביצוע", "דגשים"],
        ],
      };
    },
    methods: {
      chosenTitle(event) {
        if (event.target.tagName === "li") {
          this.titleIndex = parseInt(event.target.id.slice(-1)) - 1;
          this.$emit("chosen-page", this.titleIndex);
        }
      },
      
    },
  };
  </script>
  
  <style scoped>
  .container {
    height: 6rem;
    width: 100vw;
    display: flex;
    align-items: center;
    justify-content: center;
    align-content: flex-start;
    flex-wrap: wrap;
    margin-top: 2%;
  }
  
  * {
    margin: 0;
    box-sizing: border-box;
    z-index: 6;
  
  }
  
  nav {
    background: #fff;
    border-radius: 50px;
    box-shadow: 0 15px 20px -20px rgba(0, 0, 0, 0.4);
  }
  
  ul {
    display: flex;
    align-items: center;
    height: 10vh;
    width: 60vw;
  }
  
  nav ul li {
    padding: 0;
    list-style: none;
    display: inline-block;
    padding: 5px 50px;
    margin: 10px;
    font-size: 1.1rem;
    font-weight: 500;
    color: #777;
    position: relative;
    z-index: 2;
    cursor: default;
    transition: color 0.5s;
  }
  
  nav ul li.active {
    background: #ff87ab;
    cursor: pointer;
    border-radius: 30px;
    color: white;
  }
  
  .subject {
    font-size: 2rem;
  }
  </style>
  