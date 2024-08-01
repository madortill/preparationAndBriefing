<template>
  <div id="app">
        <img src="@/assets/media/mifkada-logo.png" class="logo" alt="Logo" @click = "homePage">
        <button v-show = "page === 0" class="aboutBtn" @click = "openAbout">i</button>
        <Transition>
          <div v-show = "showAbout" class="div-about">
          <h3 class = "list-text-about">מפתחת ראשית:</h3>
            <p class = "list-text-about">טור' דני שריקי</p>
            <h3 class = "list-text-about">גרפיקה:</h3>
            <p class = "list-text-about">טור' דני שריקי</p>
            <h3 class = "list-text-about">מומחית תוכן:</h3>
            <p class = "list-text-about">רב"ט אלה טייטלר</p>
            <h3 class = "list-text-about">רת"ח מו"פ:</h3>
            <p class = "list-text-about">רס"ל אביב אואנונו</p>
            <h3 class = "list-text-about">רמ"ד טי"ל:</h3>
            <p class = "list-text-about">רס"מ שלומי אוגרן</p>
            <h3 class = "list-text-about">גרסה:</h3>
            <p class = "list-text-about">יולי 2024</p>
        </div>
      </Transition>
        <open-screen v-if="page === 0" @next-page="nextPage"></open-screen>
        <home-page  v-if="page === 1" @next-page="nextPage"></home-page>
        <end-screen v-if="page===2" ></end-screen>

        <img src="@/assets/media/madortill.png" alt="mador-till" class="mador-till">
    </div>
</template>

<script>
import OpenScreen from '@/components/OpenScreen.vue' ; 
import HomePage from '@/components/HomePage.vue';
import EndScreen from '@/components/EndScreen.vue';



export default {
    name: "app",
    components: {
    OpenScreen,
    HomePage,
    EndScreen,
    },
    data() {
        return {
            page: 0 ,
            showAbout: false,
            clickBtn: 0,
        };
    },
    methods: {
        nextPage() {
            this.page++;
        },
        prevPage() {
            this.page--;
        },
        homePage() {
            thispage === 1;
        },
        openAbout() {
          if (this.clickBtn % 2 === 0) {
                this.showAbout = true;
            } else {
                this.showAbout = false
            }
            this.clickBtn++;
        }
    },
};

</script>

<style>

@font-face {
    font-family: 'Heebo';
    src: url('@/assets/fonts/heebo.regular.ttf');
}

@font-face {
    font-family: 'Heebo-Bold';
    src: url('@/assets/fonts/heebo.black.ttf');
}

* {
    overflow: hidden;
    font-family: 'Heebo';
}


:root {
    font-size: calc(13px + 0.4vw)
}

body {
    margin: 0;
    direction: rtl;
    background-color: #F2F2F2;
}

#app {
    font-family: 'Heebo';
    width: 100vw;
    height: 100vh;
    position: relative;
}

.logo {
    max-width: 100px;
    left: 0;
    top: 0;
    position: absolute;
    margin-top: 1%;
    margin-left: 1%;
    z-index: 3;
}

.mador-till {
    /* min-width: 20px; */
    max-height: 10%;
    max-width: 90px;
    position: absolute;
    bottom: 0;
    right: 0;
    margin-bottom: 1%;
    margin-right: 1%;
    z-index: 3;
}

.aboutBtn {
  position: absolute;
  border: none;
  color: white;
  font-size: 1.6rem;
  transition: background-color 0.3s ease;
  background-color: #02ade1;
  border-radius: 150px;
  width: 2rem;
  height: 2.5rem;
  cursor: pointer;
  left: 2.5%;
  top: 16%;
    padding: 0.2rem;
}

.aboutBtn:hover{
  background-color: #038eb9;
}
.div-about {
  position: absolute;
  width: 11rem;
  height: 27rem;
  left: 8rem;
  top: 7rem;
  background: #fff;
  border-radius: 1rem;
  box-shadow: 0 15px 20px -20px rgba(0, 0, 0, 0.4);
  text-align: center;
  z-index: 4;
}

.list-text-about {
  transition: background-color 0.5s ease;
  margin: 1rem;
}
.list-text-about:hover {
  background-color: #dbdbdb;
}

</style>
