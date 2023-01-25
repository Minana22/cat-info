<template>
  <div class="main">
    <div class="blok2">
      <button class="btn1" @click="dohvatiMacke">Get cats facts</button>
      <button class="btn2" @click="catFact">Get fact about cat</button>
    </div>
    <div class="fact">{{ oneFact }}</div>
    <div class="randomColors" v-if="factsArray && factsArray.length > 0">
      <p
        class="blok1"
        :style="{
          backgroundColor: currentColor,
        }"
        v-for="item in factsArray"
        :key="item"
      >
        {{ item.fact }}
      </p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
//const axios = require('axios'); // legacy way

// Make a request for a user with a given ID

export default {
  data: function () {
    return {
      factsArray: [],
      currentColor: "",
      oneFact: "",
    };
  },
  methods: {
    async catFact() {
      this.randomColors();
      await axios
        .get("https://catfact.ninja/fact")
        .then((response) => {
          // handle success
          console.log(response.data);
          this.oneFact = response.data.fact;
        })
        .catch(function (error) {
          // handle error
          console.log(error);
        })
        .finally(function () {
          // always executed
        });
    },

    async dohvatiMacke() {
      this.randomColors();
      await axios
        .get("https://catfact.ninja/facts")
        .then((response) => {
          // handle success
          console.log(response.data.data);
          console.log(this.factsArray);
          this.factsArray.push(...response.data.data);
        })
        .catch(function (error) {
          // handle error
          console.log(error);
        })
        .finally(function () {
          // always executed
        });
    },
    randomColors() {
      this.currentColor =
        "#" + Math.floor(Math.random() * 16777215).toString(16);
    },
  },
  mounted() {},
};
</script>

<style scoped>
.blok1 {
  height: 100px;
  width: 700px;
  font-family: Georgia, "Times New Roman", Times, serif;
  font-weight: 800;
  font-style: italic;
}
.btn1 {
  height: 40px;
  width: 80px;
  background-color: #fa78fa;
  border-radius: 1px;
  font-weight: 600;
  margin: 3px;
  padding-bottom: 10px;
}
.btn2 {
  height: 40px;
  width: 80px;
  background-color: #fa78fa;
  border-radius: 1px;
  font-weight: 600;
  margin: 3px;
  padding-bottom: 10px;
}
.blok2 {
  padding: 10px;
  align-items: center;
}
.fact {
  font-family: Georgia, "Times New Roman", Times, serif;
  font-weight: 800;

  height: 50px;
  background-color: rgba(181, 7, 170, 0.204);
}
</style>
