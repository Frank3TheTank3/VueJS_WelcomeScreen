<template>
  <!--APP-->
  <div id="app" class="">
    <!--Main Container-->
    <div id="maincontainer">
      <!--Welcome & Title-->
      <div class="welcome glow">
        <h1 class="welcometext">Welcome to</h1>
        <img class="logo" src="./assets/logo_op.png" />
        <img class="logo_spark" src="./assets/stars.gif" />
      </div>

      <!--Date-->
      <h1 class="date">{{ getDate() }}</h1>
      <!-- <p>{{  entries}}</p>
      <p>{{  entries[0]}}</p> -->
      <!--
      
       <p>{{  entries}}</p> -->

      <!--Main Activity List-->
      <div v-if="entries">
        <ul class="list">
          <li
            class="center marked"
            v-for="entry in entries.slice(1)"
            :key="entry"
          >
            <p class="fat shadow">
              {{ entry[0] }} {{ entry[1].replaceAll("/", ".") }}
            </p>
            <p class="title">{{ entry[2] }}</p>
            <p>{{ entry[3] }}</p>
          </li>
        </ul>
      </div>

      <div v-else class="center">
        <h1 class="slowglow">
          Our hamster powered servers stopped running. There's no data available
          at the moment.
        </h1>
        <img class="marked hamster" src="./assets/hamster4.gif" />
      </div>
    </div>

    <!--Footer-->
    <div class="footer center">
      <img class="logo2 logopos" src="./assets/logo_soz.svg" />
      <img class="logo2" src="./assets/logo_opport.png" />
      <img class="logo2 logopos" src="./assets/logo_sag.png" />
    </div>
  </div>
</template>

<script>
import axios from "axios"; // axios is a library for making HTTP requests to the backend

export default {
  name: "App",
  data() {
    return {
      title: "Welcome to Opportunity",
    
     sheet_id: "",
     api_token: "",

      entries: undefined,
      currentDate: "",
    };
  },
  computed: {
    // computed properties are like data properties, but with a method combined and it gets executed automatically, instead of calling a function explicitly
    gsheet_url() {
      return `https://sheets.googleapis.com/v4/spreadsheets/${this.sheet_id}/values:batchGet?ranges=A2%3AE100&valueRenderOption=FORMATTED_VALUE&key=${this.api_token}`;
    },
  },
  methods: {
    getDate() {
      const currentDate = new Date();
      const currentMonth = currentDate.getMonth() + 1;
      let zeroDigit = "";
      if (currentMonth < 10) {
        zeroDigit = ".0";
      }
      const date =
        currentDate.getDate() +
        zeroDigit +
        currentMonth +
        "." +
        currentDate.getFullYear();
      return date;
    },

    getData() {
      axios.get(this.gsheet_url).then((response) => {
        this.entries = response.data.valueRanges[0].values;
      });
    },

    refreshData() {
      this.getData();
      this.getDate();
    },
  },

  mounted() {
    this.getData();
    
    setInterval(() => {
      this.refreshData();
    }, 1800000);
    
  },
};
</script>

<!--Style-->
<style>
@import url("https://fonts.googleapis.com/css2?family=Inter&display=swap");
/* App / Center-Class / Main Container / Footer*/
#app {
  font-family: Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  display: inline-block;
  font-family: "Inter";
}

.center {
  margin: auto;
  width: 50%;
  padding: 10px;
}

#maincontainer {
  display: block;
  background-color: rgb(214, 229, 234);
  height: 1920px;
  max-width: 1080px;
  width: 100%;
}

.footer {
  margin: auto;
  align-content: center;
  align-items: center;
  display: flex;
  position: absolute;
  width: 1080px;
}

/*Welcome Text & Date & Button / Labels*/

.addNew {
  display: block;
  padding: 25px;
  align-content: center;
  text-align: center;
}

.button {
  display: flex;
  padding: 25px;
  justify-content: center;
}
button {
  width: 150px;
  height: 60px;
  text-align: center;
}
label {
  padding: 25px;
  font-size: 30px;
}

.welcometext {
  transform: translateY(35%);
  right: 200px;
}

.welcome {
  display: inline-flex;
  align-content: center;
  padding-left: 10%;
  font-family: Impact, Haettenschweiler, "Arial Narrow Bold", sans-serif;
  text-transform: uppercase;
}

.date {
  display: block;
  margin-left: auto;
  margin-right: auto;
  text-align: left;
  margin-left: 8%;
  font-size: 60px;
  color: #797c7e;
  font-weight: 100;
}

/*Logos*/

.logo2 {
  width: 100%;
  min-height: 100%;
  min-width: 5%;
  margin: 50px;
  text-align: center;
  vertical-align: middle;
}

.logo_spark {
  position: absolute;
  left: 45%;
  top: -5%;
}

.logopos {
  transform: translateY(22%);
}

.logo {
  display: block;
  margin-left: auto;
  margin-right: auto;
  height: 120px;
  width: 70%;
}

.hamster {
  position: relative;
  left: 15px;
  width: 500px;
  height: 400px;
}

/*List tag customization*/

.list li {
  list-style-type: none;
  background-color: rgb(32, 26, 140);
  font-size: 30px;
  color: rgb(181, 97, 29);
  margin: 50px;
  line-height: 150px;
  padding: 20px;
  width: auto;
  animation: fadeOutUp 0.5s ease-in forwards;
}

.list li:hover {
  list-style-type: none;
  background-color: rgb(77, 71, 190);
  font-size: 30px;
  color: rgb(255, 255, 255);
  margin: 50px;
  line-height: 150px;
  padding: 20px;
  width: auto;
  animation: fadeInDown 0.5s ease-in forwards;
}

/* Keyframe Animation */

@keyframes fadeInDown {
  from {
    transform: translate(0, 0%);
  }
  to {
    transform: translate(0, -10%);
  }
}

@keyframes fadeOutUp {
  from {
    transform: translate(0, -10%);
  }
  to {
    transform: translate(0, 0%);
  }
}

@keyframes fadeInSide {
  from {
    opacity: 0;
    transform: translate(-100%, 0);
  }
  to {
    opacity: 1;
    transform: translate(0, 0);
  }
}

/* P tag & Title color and font styles */

p {
  margin: 0;
  line-height: 50px;
}

.fat {
  font-weight: bold;
  color: rgb(236, 25, 32);
}

.title {
  font-weight: bold;
  color: rgb(224, 138, 107);
}

/* Effects for Text */

.slowglow {
  text-align: center;
  -webkit-animation: glow 1s ease-in-out infinite alternate;
  -moz-animation: glow 1s ease-in-out infinite alternate;
  animation: slowglow 5s ease-in-out infinite alternate;
}

.glow {
  text-align: center;
  -webkit-animation: glow 1s ease-in-out infinite alternate;
  -moz-animation: glow 1s ease-in-out infinite alternate;
  animation: glow 1s ease-in-out infinite alternate;
}

@-webkit-keyframes glow {
  from {
    text-shadow: 0 0 10px #ed6808, 0 0 20px #ed6808, 0 0 30px #ed6808,
      0 0 40px #ed6808, 0 0 50px #ed6808, 0 0 60px #ed6808, 0 0 70px #ed6808;
    color: #fff;
  }
  to {
    text-shadow: 0 0 20px #fff, 0 0 30px #fff, 0 0 40px #fff, 0 0 50px #fff,
      0 0 60px #fff, 0 0 70px #fff, 0 0 80px #fff;
  }
}

@-webkit-keyframes slowglow {
  from {
    text-shadow: 0 0 10px #089c88, 0 0 20px #089c88, 0 0 30px #089c88,
      0 0 40px #089c88, 0 0 50px #089c88, 0 0 60px #089c88, 0 0 70px #089c88;
    color: #fff;
  }
  to {
    text-shadow: 0 0 20px #fff, 0 0 30px #fff, 0 0 40px #fff, 0 0 50px #fff,
      0 0 60px #fff, 0 0 70px #fff, 0 0 80px #fff;
  }
}

.shadow {
  text-shadow: -1px -1px 0 #fff, 1px -1px 0 #fff, -1px 1px 0 #fff,
    1px 1px 0 #fff;
}

.marked {
  outline: 5px solid #ed6808;
}
</style>
