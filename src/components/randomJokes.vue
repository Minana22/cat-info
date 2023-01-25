<template>
  <div class="main">
    <button class="btn" @click="dohvatiJokes">Get jokes</button>
    <div class="jokes" v-if="factsArray && factsArray.length > 0">
      <p class="parag" v-for="item in factsArray" :key="item">
        {{ item.type }}: {{ item.setup }} {{ item.punchline }}
      </p>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data: function () {
    return {
      factsArray: [],
    };
  },
  methods: {
    async dohvatiJokes() {
      await axios
        .get("https://official-joke-api.appspot.com/jokes/ten")
        .then((response) => {
          // handle success
          console.log(response.data);
          console.log(this.factsArray);
          this.factsArray.push(...response.data);
        })
        .catch(function (error) {
          // handle error
          console.log(error);
        })
        .finally(function () {
          // always executed
        });
    },
  },
};
</script>
<style scoped>
.parag {
  font-family: Cambria, Cochin, Georgia, Times, "Times New Roman", serif;
  font-style: italic;
  font-size: medium;
  font-weight: 600;
}
.jokes {
  background-color: #740698;
  background-image: linear-gradient(0deg, #d9afd9 0%, #97d9e1 100%);
}
.btn {
  height: 40px;
  width: 80px;
  background-color: #fa78fa;
  border-radius: 1px;
  font-weight: 600;
  margin: 3px;
}
</style>
