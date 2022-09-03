<script>
import axios from "axios";
import { assertExpressionStatement } from '@babel/types';

export default {
  data: function () {
    return {
      message1: "HELLO!!",

    };
  },
  created: function () { },
  methods: {

  }
}
</script>


<template>
  <div class="container">
    <div class="home">
      <div id="app">
        <h1><b>{{ message1 }}</b></h1>
        <main>
          <div class="search-box">
            <input type="text" class="search-bar" placeholder="Search...">
          </div>
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
</style>