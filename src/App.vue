<template>
  <div id="app">
    <div id="maincontainer">
      <div class="welcome">
    <h1 class="welcometext">Welcome to</h1>
    <img alt="Vue logo" class="logo" src="./assets/logo_op.png" />
</div>
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <h1 class="date">{{ date }}</h1>
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

    <div class="footer">
    <img alt="Vue logo" class="logo2 logopos" src="./assets/logo_soz.svg" />
    <img alt="Vue logo" class="logo2" src="./assets/logo_opport.png" />
    <img alt="Vue logo" class="logo2 logopos" src="./assets/logo_sag.png" />
    </div>
  </div>
</template>

<script>

export default {
  name: "App",

  data() {
    let currentDate = new Date();
    let cDay = currentDate.getDate();
    let cMonth = currentDate.getMonth() + 1;
    let cYear = currentDate.getFullYear();
    return {
      date: cDay + ".0" + cMonth + "." + cYear,
    };
  }

};
</script>

<style>
#app {
  font-family: Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
 
}

#maincontainer{

 background-color: rgb(214, 229, 234);
  height: 1920px;
  width: 1080px;

}

.welcometext{
 transform: translateY(45%);
 right: 200px;
}

.footer{
  display: inline;
  align-content: center;

}

.welcome{
  display: inline-flex;
  align-content: center;
  padding-left: 10%;

}
.logo2{
width:250px;
margin: 50px;
text-align: center;
vertical-align: middle;
}

.logopos{
 transform: translateY(20%);
}

.date{
   display: block;
  margin-left: auto;
  margin-right: auto;
   text-align: left;
   margin-left: 8%;
   font-size: 60px;
   color: #797c7e;
   font-weight: 100;
}

.logo {
  display: block;
  margin-left: auto;
  margin-right: auto;
  height: 150px;
  width: 70%;
  
}

.list li {
  list-style-type: none;
  background-color: rgb(32, 26, 140);
  font-size: 30px;
  color: rgb(181, 97, 29);
  margin: 50px;
  line-height: 150px;
  padding: 20px;
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
