<script>
import axios from "axios";
import { assertExpressionStatement } from '@babel/types';

export default {
  data: function () {
    return {
      message1: "HELLO!!",
      weathers: {},
      weather: {},
      params: {},
    };
  },
  created: function () { },
  methods: {
    submit: function (params) {
      console.log('weathers index');
      console.log(this.params);
      var params = this.params
      var weathers = axios.get("/weathers.json", { params }).then(response => {
        console.log(response.data);
        this.weathers = response.data;

      })
    },
    dateBuilder() {
      let d = new Date();
      let months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
      let days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
      let day = days[d.getDay()];
      let date = d.getDate();
      let month = months[d.getMonth()];
      let year = d.getFullYear();
      return `${day} ${date} ${month} ${year}`;
    }
  }
}


</script>


<template>
  <div class="container">
    <div class="home">
      <div id="app">
        <h1><b>{{ message1 }}</b></h1>

        <main>
          <form v-on:submit.prevent="submit()">
            <div class="search-box">
              <input type="text" class="search-bar" placeholder="Search..." v-model="params.city">


            </div>
            <div class="weather-wrap" v-if="typeof weathers.main != 'undefined'">
              <div class="location-box">
                <div class="location">
                  {{ weathers.name }}, {{ weathers.sys.country }}
                  <div class="date">{{ dateBuilder() }}</div>
                </div>
              </div>

              <div class="weather-box">
                <div class="temp">{{ Math.round(this.weathers.main.temp) }}</div>
                <div class="weather">{{ weathers.weather[0].main }}</div>

              </div>
            </div>

          </form>
        </main>
      </div>

    </div>
  </div>

</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'montserrat', sans-serif;
}

#app {
  background-image: url('../assets/cold-bg.jpeg');
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}

#app.warm {
  background-image: url('../assets/warm-bg.jpeg');
}

main {
  min-height: 100vh;
  padding: 25px;
  background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.25), rgba(0, 0, 0, 0.75));
}

.search-box {
  width: 100%;
  margin-bottom: 30px;
}

.search-box .search-bar {
  display: block;
  width: 100%;
  padding: 15px;

  color: #313131;
  font-size: 20px;
  appearance: none;
  border: none;
  outline: none;
  background: none;
  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 0px 16px 0px 16px;
  transition: 0.4s;
}

.search-box .search-bar:focus {
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.75);
  border-radius: 16px 0px 16px 0px;
}

.location-box .location {
  color: #FFF;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}

.location-box .date {
  color: #FFF;
  font-size: 20px;
  font-weight: 300;
  font-style: italic;
  text-align: center;
}

.weather-box {
  text-align: center;
}

.weather-box .temp {
  display: inline-block;
  padding: 10px 25px;
  color: #FFF;
  font-size: 102px;
  font-weight: 900;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.25);
  border-radius: 16px;
  margin: 30px 0px;
  box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}

.weather-box .weather {
  color: #FFF;
  font-size: 48px;
  font-weight: 700;
  font-style: italic;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}
</style>