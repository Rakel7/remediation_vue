<template>
  <Header />
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Welcome to Your Phone book Dev App" />
  <button @click="getList">Appel Api</button>
  <div id="app-vue">
    <div class="users">
      <div v-if="errored">
        <p>
          We're sorry, we're not able to retrieve this information at the
          moment, please try back later
        </p>
      </div>

      <div v-else class="cards">
        <h4 v-if="loading">Loading...</h4>
        <Card
          v-for="result in results"
          :key="result.id"
          :picture="result.picture"
          :name="result.name"
          :email="result.email"
          :phone="result.phone"
          class="userCard"
        />
      </div>
    </div>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import Header from "./components/Header.vue";
import axios from "axios";
import Card from "./components/Card.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
    Header,
    Card,
  },

  data() {
    return {
      results: [],
      loading: false,
      errored: false,
    };
  },
  methods: {
    getList() {
      axios.get("https://randomuser.me/api/?results=12").then((response) => {
        this.results = response.data.results;
        console.log(response.data.results);
      });
    },
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
#app-vue {
  display: flex;
  justify-content: center;
  font-family: "Karla", sans-serif;
  font-size: 20px;
}

.userCard {
  width: 300px;
  border: 1px solid black;
  padding: 20px;
  background: #ffeee4;
  margin: 10px;
}

.cards {
  margin: 0 auto;
  display: grid;
  grid-template-columns: 400px 400px 400px;
}
</style>
