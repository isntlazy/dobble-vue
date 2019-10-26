<template>
  <div class="select-container">
    <h4>Виберіть спільний елемент:</h4>
    <div class="select-elements">
      <div @click="itemClicked(item)" class="darken" :key="index" v-for="(item, index) in items">
        <img class="element" :src="require(`../assets/${item}.svg`)" :alt="item">
      </div>
    </div>
  </div>
</template>
<script>
	export default {
		name: 'SelectContainer',
		props: ['items', 'commonItem'],
    methods: {
	    itemClicked(item) {
	    	if (item === this.commonItem) {
			    this.$emit('nextCard');
        }
      }
    }
	}
</script>

<style lang="scss">
  @import "../assets/scss/general.scss";
  .select-container {
    max-width: 50%;
    flex: 0 0 50%;
  }
  .select-elements {
    padding:  calc-size-desktop(10);
  }
  .element {
    margin:  calc-size-desktop(10);
    max-width:  calc-size-desktop(100);
    max-height:  calc-size-desktop(52);
  }
  .darken {
    display: contents;
    background: black;
    padding: 0;
    cursor: pointer;
  }
  div.darken img {
    transition: all 0.3s linear;
  }

  div.darken:hover img {
    opacity: 0.6;
  }
  @media (max-width: 768px) {
    .select-container {
      flex: 0 0 100%;
      max-width: 100%;
    }

    .select-elements {
      padding:  calc-size-mobile(5);
    }
    .element {
      margin:  calc-size-mobile(5);
      max-width:  calc-size-mobile(70);
      max-height:  calc-size-mobile(30);
    }
  }


</style>
