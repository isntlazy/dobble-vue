<template>
  <div class="circle">
    <img class="element" :class="`element-${++index}`" :key="index" v-for="(item, index) in items" :src="require(`../assets/${item}.svg`)" :alt="item">
  </div>
</template>

<script>
export default {
	props: ['items']
}
</script>

<style scoped>
  .circle {
    position: relative;
    border-radius: 50%;
    width: 280px;
    height: 280px;
    background: white;
    border: 2px solid black;
    margin: 15px 15px 15px 40px;
  }
  .element {
    position: absolute;
    max-width: 100px;
    max-height: 55px;
  }
  .element-1 {
    top: 15px;
    left: 95px;
  }
  .element-2 {
    top: 80px;
    left: 40px;
  }
  .element-3 {
    top: 150px;
    left: 40px;
  }
  .element-4 {
    top: 210px;
    left: 110px;
  }
  .element-5 {
    top: 70px;
    left: 160px;
  }
  .element-6 {
    top: 150px;
    left: 160px;
  }
</style>
