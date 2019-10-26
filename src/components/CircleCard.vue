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
    width: calc(300 / 1680 * 100vw);
    height: calc(300 / 1680 * 100vw);
    background: white;
    /*margin: calc(15 / 1680 * 100vw) calc(15 / 1680 * 100vw) calc(15 / 1680 * 100vw) calc(40 / 1680 * 100vw);*/
    box-shadow: 1px 0.5px 1px 0px #ffffff inset, 0px 1px 5px 0px #B3B3B3
  }

  .circle:first-of-type {
    margin-left: calc(40 / 1680 * 100vw);
  }

  .circle:last-of-type {
    margin-right: calc(40 / 1680 * 100vw);
  }

  .element {
    position: absolute;
    max-width: calc(100 / 1680 * 100vw);
    max-height: calc(55 / 1680 * 100vw);
  }
  .small {
    max-width: calc(75 / 1680 * 100vw) !important;
    max-height: calc(40 / 1680 * 100vw) !important;
  }
  .element-1 {
    top: calc(15 / 1680 * 100vw);
    left: calc(95 / 1680 * 100vw);
  }
  .element-2 {
    top: calc(80 / 1680 * 100vw);
    left: calc(40 / 1680 * 100vw);
  }
  .element-3 {
    top: calc(150 / 1680 * 100vw);
    left: calc(40 / 1680 * 100vw);
  }
  .element-4 {
    top: calc(210 / 1680 * 100vw);
    left: calc(103 / 1680 * 100vw);
  }
  .element-5 {
    top: calc(70 / 1680 * 100vw);
    left: calc(155 / 1680 * 100vw);
  }
  .element-6 {
    top: calc(150 / 1680 * 100vw);
    left: calc(160 / 1680 * 100vw)
  }
  @media (max-width: 480px) {
    .circle {
      width: calc(165 / 375 * 100vw);
      height: calc(165 / 375 * 100vw);
    }

    .circle:first-of-type {
      margin-left: calc(15 / 375 * 100vw);
    }

    .circle:last-of-type {
      margin-right: calc(15 / 375 * 100vw);
    }

    .element {
      position: absolute;
      max-width: calc(52 / 375 * 100vw);
      max-height: calc(28 / 375 * 100vw);
    }
    .small {
      max-width: calc(39 / 375 * 100vw) !important;
      max-height: calc(21 / 375 * 100vw) !important;
    }
    .element-1 {
      top: calc(10 / 375 * 100vw);
      left: calc(50 / 375 * 100vw);
    }
    .element-2 {
      top: calc(40 / 375 * 100vw);
      left: calc(20 / 375 * 100vw);
    }
    .element-3 {
      top: calc(80 / 375 * 100vw);
      left: calc(20 / 375 * 100vw);
    }
    .element-4 {
      top: calc(110 / 375 * 100vw);
      left: calc(55 / 375 * 100vw);
    }
    .element-5 {
      top: calc(35 / 375 * 100vw);
      left: calc(80 / 375 * 100vw);
    }
    .element-6 {
      top: calc(80 / 375 * 100vw);
      left: calc(85 / 375 * 100vw)
    }
  }
</style>
