<template>
  <div id="app">
    <h1>Доббл Веб</h1>
    <GameContainer />
  </div>
</template>

<script>
import GameContainer from './components/GameContainer.vue';

export default {
  name: 'app',
  components: {
    GameContainer,
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: calc(60 / 2880 * 100vw);
}
body {
  margin: 0;
}
@media (max-width: 480px) {
  h1 {
    font-size: calc(22 / 375 *100vw);
    text-align: left;
    margin-left: calc(15 / 375 *100vw);;
  }
}
</style>
