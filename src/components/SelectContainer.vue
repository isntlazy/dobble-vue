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

<style>
  .select-container {
    max-width: 50%;
    flex: 0 0 50%;
  }
  .select-elements {
    padding:  calc(10 / 1680 * 100vw);
  }
  .element {
    margin:  calc(10 / 1680 * 100vw);
    max-width:  calc(100 / 1680 * 100vw);
    max-height:  calc(52 / 1680 * 100vw);
  }
  .darken {
    display: contents;
    background: black;
    padding: 0;
    cursor: pointer;
  }
  div.darken img {
    -webkit-transition: all 0.3s linear;
    -moz-transition: all 0.3s linear;
    -ms-transition: all 0.3s linear;
    -o-transition: all 0.3s linear;
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
      padding:  calc(5 / 375 * 100vw);
    }
    .element {
      margin:  calc(5 / 375 * 100vw);
      max-width:  calc(70 / 375 * 100vw);
      max-height:  calc(30 / 375 * 100vw);
    }
  }


</style>
