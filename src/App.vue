<template v-bind:style="{ 'background-color': color}">
  <div id="app">
    <header>
    </header>
    <main>
      <h1 id="title">{{ title }}</h1>
      
      <p id="date">{{ currentDate() }}</p>


      <ul id="listBox">
        <li v-for="entry in entries" :key="entry">
          <p><span id="itemTime" >{{ entry[0] }}, {{ entry[1] }}</span></p>
          <h3 id="item">{{ entry[2] }}</h3>
          <p><span id="itemDescription">I{{ entry[3] }}</span></p>
          </li>
      </ul>
      </main>
      <footer>
        <img id="img1" src="./assets/STZH_SEB_Logo.png">
        <img id="img2" src="./assets/Opportunity.png">
        <img id="img3" src="./assets/SAG_Logo_De.png">
      </footer>

  </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'App',
  data() {
    return {
    title: "Welcome to Opportunity",
    sheet_id: "1a81aI0Y8ViZO0tI92h2YSMqVQJ8hmNNMyMylXgvwiU4",
    api_token: "AIzaSyA-qeDXOhEeQDA0vQf7LgkF7DQtGnAtmAU",
    entries: [],
    }
  },

  computed: {
    gsheet_url() {
      return `https://sheets.googleapis.com/v4/spreadsheets/${this.sheet_id}/values:batchGet?ranges=A2%3AE100&valueRenderOption=FORMATTED_VALUE&key=${this.api_token}`;
    }
  },

  methods: {
    getData() {
      axios.get(this.gsheet_url).then((response) => {
        this.entries = response.data.valueRanges[0].values;
      });
    },

    currentDate() {
      const current = new Date();
      const day = current.getDate();
      const month = (current.getMonth()+1);
      const year = current.getFullYear();
      const dateTime = day + "." + month + "." + year;
      if (month < 10) {
        return day + "." + "0" + month + "." + year;
      }
      return dateTime;
    },
  
      // dateStringReplace() {
      //   this.entries = this.entries.replace("/", ".");
      // }
  },

  mounted() {
    this.getData();
  }
};
</script>

<style>
/* @font-face {
  font-family: 'Inter';
  src: url('~@/assets/Inter-VariableFont_slnt,wght.ttf');
} */

@import url('https://fonts.googleapis.com/css2?family=Inter:wght@500;900&display=swap');


* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Inter', Arial, Helvetica, Arial, sans-serif;
}

#app {
  background-color:#E8EFF4;
}

h1 {
position: static;
width: 100%;
padding: 5.5vw 2vw 0vw;
font-weight: 900;
font-size: 62px;
line-height: 75px;
color: #323D4A;
}

#date {
position: relative;
padding: 2vw 2vw;
font-family: 'Inter';
font-style: normal;
font-weight: 500;
font-size: 62px;
line-height: 75px;
color: #9AA7B1;
}

#listBox {
position: relative;
margin: 0vw 2vw 0vw;
}

li {
position: relative;
margin-bottom: 30px;
padding: 3vw;
background: #0F05A0;
list-style-type: none;
}

img {
    height: 5vw;
}

#img1 {
  position: absolute;
  left: 5.5vw;
}

#img2 {
  position: absolute;
  left: 34vw;
}

#img3 {
  position: absolute;
  left: 67vw;
}

#item {
  font-weight: 900;
  font-size: 28px;
  line-height: 36px;
  color: #fca66c;;
}

#itemTime {
  font-weight: 900;
  font-size: 28px;
  line-height: 36px;
  color: #EB5E00;
}

#itemDescription {
  font-weight: 500;
  font-size: 28px;
  line-height: 36px;
  color: #fca66c;
}

main {
  min-height: 100vh;
  margin-left: 5.5vw;
  margin-right: 5.5vw;
}

footer {
  position: fixed;
  left: 0px;
  right: 0px;
  bottom: 0px;
  height: 130px;
  padding: 4vw ;
  background-color: white;
}
</style>
