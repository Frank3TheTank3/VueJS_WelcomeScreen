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
        <li class="center">
          <p class="fat">14 00 Uhr 07.08.2021</p>
          <p class="title">Basisbeschäftigung Besuch</p>
          <p>Interessierte für den zweiten Kurs werden uns besuchen</p>
        </li>
        <li class="center">
          <p class="fat">15 30 Uhr 09.08.2021</p>
          <p class="title">Firmenbesuch Microsoft</p>
          <p>Roger Halbheer, Head of Security</p>
        </li>
        <li class="center">
          <p class="fat">8 30 Uhr 10.08.2021</p>
          <p class="title">Tugce Nur returns to Office</p>
          <p>We will continue working on this app together on Tuesday!</p>
        </li>
      </ul>
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

  data() {
    let currentDate = new Date();
    let cDay = currentDate.getDate();
    let cMonth = currentDate.getMonth() + 1;
    let cYear = currentDate.getFullYear();
    return {
      date: cDay + ".0" + cMonth + "." + cYear,
    };
  },
};
</script>

<!--Style-->
<style>

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

/*Welcome Text & Date*/

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
  width: 200px;
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
