<template>
  <div class="circle">
    <img :class="[{small: isSmall()}, 'element-' + (index + 1)]"
         class="element"
         :key="index"
         v-for="(item, index) in items"
         :src="require(`../assets/${item}.svg`)"
         :alt="item"
    >
  </div>
</template>

<script>
export default {
	props: ['items'],
  methods: {
		isSmall() {
			return  Math.random() < 0.4;
    }
  }
}
</script>

<style scoped>
  .circle {
    position: relative;
    border-radius: 50%;
    width: 280px;
    height: 280px;
    background: white;
    margin: 15px 15px 15px 40px;
    box-shadow: 1px 0.5px 1px 0px #ffffff inset, 0px 1px 5px 0px #B3B3B3
  }
  .element {
    position: absolute;
    max-width: 100px;
    max-height: 55px;
  }
  .small {
    max-width: 75px !important;
    max-height: 40px !important;
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
    left: 103px;
  }
  .element-5 {
    top: 70px;
    left: 155px;
  }
  .element-6 {
    top: 150px;
    left: 160px;
  }
</style>
