<template>
  <div class="main">
    <div class="show">
      <button class="btnShow" @click="showHelloWorld = !showHelloWorld">
        Cats/jokes
      </button>
    </div>
    <HelloWorld v-if="showHelloWorld" />
    <randomJokes v-else></randomJokes>
  </div>
</template>

<script>
import randomJokes from "./components/randomJokes.vue";
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
    randomJokes,
  },
  data() {
    return {
      showHelloWorld: true,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.main {
  display: flex;
  flex-direction: column;

  width: 100%;
  height: 100vh;
  background: rgb(222, 186, 239);
  justify-content: flex-start;
  align-items: center;
}
.show {
  width: 200px;
  height: 100px;
  align-items: center;
  justify-content: center;
}
.btnShow {
  width: 80px;
  height: 50px;
  font: 15px;
  font-weight: 600;
  background-color: rgb(188, 121, 251);
}
</style>
