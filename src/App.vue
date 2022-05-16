<template>
  <!--APP-->
  <div id="app" class="center">
    <!--Main Container-->
    <div id="maincontainer">
      <!--Welcome & Title-->
      <div class="welcome">
        <h1 class="welcometext">Welcome to</h1>
        <img class="logo" src="./assets/logo_op.png" />
      </div>

      <!--Date-->
      <h1 class="date">{{ date }}</h1>

      <!--Main Activity List-->
      <ul class="list">
        <li class="center" v-for="post in allPosts" :key="post">
          <p class="fat">{{ post.postDate }}</p>
          <p class="title">{{ post.postEvent }}</p>
          <p>{{ post.postDes }}</p>
        </li>
      </ul>
      <div class="addNew">
      <label for="dateInput">Date:</label>
      <br>
      <input id="dateInput" class="center" type="text">
      <br>
      <label for="dateInput">Event:</label>
      <br>
      <input id="dateInput" class="center" type="text">
      <br>
      <label for="dateInput">Description:</label>
      <br>
      <input id="dateInput" class="center" type="text">
      <br>
      <div class="button">
      <button > Submit New Event </button>
      </div>
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

<!--Scripts-->
<script>
export default {
  name: "OpportunityWelcomeScreen",

  allPosts: [],

  data() {
    let currentDate = new Date();
    let cDay = currentDate.getDate();
    let cMonth = currentDate.getMonth() + 1;
    let cYear = currentDate.getFullYear();
    return {
      date: cDay + ".0" + cMonth + "." + cYear,
      allPosts: [
        {
          postDate: "14 00 Uhr 07.08.2021",
          postEvent: "Basisbeschäftigung Besuch",
          postDes: "Interessierte für den zweiten Kurs werden uns besuchen",
        },
        {
          postDate: "15 30 Uhr 09.08.2021",
          postEvent: "Firmenbesuch Microsoft",
          postDes: "Roger Halbheer, Head of Security",
        },
        {
          postDate: "8 30 Uhr 10.08.2021",
          postEvent: "Tugce Nur returns to Office",
          postDes: "We will continue working on this app together on Tuesday!",
        },
      ],
    };
  },

  methods: {
    /*
    addNewEvent (eventDate, eventName, eventDes){

      allPosts.push(eventDate, eventName, eventDes)
    }
*/

  }
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
  margin-top: 60px;
}

.center {
  font-family: "Inter";
  margin: auto;
  width: 50%;
  padding: 10px;
}

#maincontainer {
  background-color: rgb(214, 229, 234);
  height: 1920px;
  width: 1080px;
}

.footer {
  margin: auto;
  align-content: center;
  display: inline;
  margin-left: 50px;
}

/*Welcome Text & Date & Button / Labels*/

.addNew{
  display: block;
  padding: 25px;
  align-content: center;
  text-align: center;

}

.button{
 
  display:flex;
  padding: 25px;
  justify-content: center;
}
button{
   width: 150px;
   height: 60px;
   text-align: center;
}
label{
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
  width: 180px;
  margin: 50px;
  text-align: center;
  vertical-align: middle;
}

.logopos {
  transform: translateY(20%);
}

.logo {
  display: block;
  margin-left: auto;
  margin-right: auto;
  height: 120px;
  width: 70%;
}

/*List tag / P tag & title color and font styles*/

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
</style>
