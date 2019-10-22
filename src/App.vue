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
  margin-top: 60px;
}
</style>
