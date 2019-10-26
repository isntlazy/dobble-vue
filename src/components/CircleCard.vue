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

<style lang="scss" scoped>
  @import "../assets/scss/general.scss";
  .circle {
    position: relative;
    border-radius: 50%;
    width: calc-size-desktop(300);
    height: calc-size-desktop(300);
    background: white;
    box-shadow: 1px 0.5px 1px 0px #ffffff inset, 0px 1px 5px 0px #B3B3B3
  }

  .circle:first-of-type {
    margin-left: calc-size-desktop(40);
  }

  .circle:last-of-type {
    margin-right: calc-size-desktop(40);
  }

  .element {
    position: absolute;
    max-width: calc-size-desktop(100);
    max-height: calc-size-desktop(55);
  }
  .small {
    max-width: calc-size-desktop(75) !important;
    max-height: calc-size-desktop(40) !important;
  }
  .element-1 {
    top: calc-size-desktop(15);
    left: calc-size-desktop(95);
  }
  .element-2 {
    top: calc-size-desktop(80);
    left: calc-size-desktop(40);
  }
  .element-3 {
    top: calc-size-desktop(150);
    left: calc-size-desktop(40);
  }
  .element-4 {
    top: calc-size-desktop(210);
    left: calc-size-desktop(103);
  }
  .element-5 {
    top: calc-size-desktop(70);
    left: calc-size-desktop(155);
  }
  .element-6 {
    top: calc-size-desktop(150);
    left: calc-size-desktop(160);
  }
  @media (max-width: 768px) {
    .circle {
      width: calc-size-mobile(165);
      height: calc-size-mobile(165);
    }

    .circle:first-of-type {
      margin-left: calc-size-mobile(15);
    }

    .circle:last-of-type {
      margin-right: calc-size-mobile(15);
    }

    .element {
      position: absolute;
      max-width: calc-size-mobile(52);
      max-height: calc-size-mobile(28);
    }
    .small {
      max-width: calc-size-mobile(45) !important;
      max-height: calc-size-mobile(25) !important;
    }
    .element-1 {
      top: calc-size-mobile(10);
      left: calc-size-mobile(50);
    }
    .element-2 {
      top: calc-size-mobile(40);
      left: calc-size-mobile(20);
    }
    .element-3 {
      top: calc-size-mobile(80);
      left: calc-size-mobile(20);
    }
    .element-4 {
      top: calc-size-mobile(110);
      left: calc-size-mobile(55);
    }
    .element-5 {
      top: calc-size-mobile(35);
      left: calc-size-mobile(80);
    }
    .element-6 {
      top: calc-size-mobile(80);
      left: calc-size-mobile(85);
    }
  }

  @media (max-width: 480px) {
    .circle {
      width: calc-size-mobile(190);
      height: calc-size-mobile(190);
      margin: calc-size-mobile(10) 0 !important;
    }

    .element {
      position: absolute;
      max-width: calc-size-mobile(62);
      max-height: calc-size-mobile(38);
    }
    .small {
      max-width: calc-size-mobile(55) !important;
      max-height: calc-size-mobile(35) !important;
    }
    .element-1 {
      top: calc-size-mobile(10);
      left: calc-size-mobile(50);
    }
    .element-2 {
      top: calc-size-mobile(50);
      left: calc-size-mobile(20);
    }
    .element-3 {
      top: calc-size-mobile(90);
      left: calc-size-mobile(20);
    }
    .element-4 {
      top: calc-size-mobile(130);
      left: calc-size-mobile(65);
    }
    .element-5 {
      top: calc-size-mobile(35);
      left: calc-size-mobile(110);
    }
    .element-6 {
      top: calc-size-mobile(80);
      left: calc-size-mobile(105);
    }
  }
</style>
