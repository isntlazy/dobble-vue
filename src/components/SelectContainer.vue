<template>
  <div class="select-container">
    <h2>Залишилось: {{ countDown }} секунд</h2>
    <h4>Виберіть спільний елемент:</h4>
    <div class="select-elements">
      <div class="darken" :key="index" v-for="(item, index) in items">
        <img class="element" :src="require(`../assets/${item}.svg`)" :alt="item">
      </div>
    </div>
  </div>
</template>
<script>
	export default {
		name: 'SelectContainer',
		props: ['items'],
    data() {
			return {
				countDown : 60
      }
    },
		mounted() {
			this.countDownTimer()
		},
    methods: {
	    countDownTimer() {
		    if (this.countDown > 0) {
			    setTimeout(() => {
				    this.countDown -= 1;
				    this.countDownTimer()
			    }, 1000)
		    } else {
		    	this.$emit('endOfTime');
        }
	    },
    }
	}
</script>

<style>
  .select-container {
    max-width: 50%;
  }
  .select-elements {
    padding: 10px;
  }
  .element {
    margin: 10px;
    max-width: 100px;
    max-height: 52px;
  }
  .darken {
    display: contents;
    background: black;
    padding: 0;
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
</style>
