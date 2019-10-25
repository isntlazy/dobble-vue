<template>
  <div>
    <div class="new-game" v-show="newGame">
      <br>
      <p class="description">
        Доббл - це гра, у якій вам потрібно знайти один елемент (зображення), який присутній на двох картках одночасно.
        У ролі елементів виступають логотипи відомих веб-технологій, таких як:
        <br>
        <br>
        <img class="element" :src="require(`../assets/vue.svg`)">
        <img class="element" :src="require(`../assets/node.svg`)">
        <img class="element" :src="require(`../assets/react.svg`)">
      </p>
      <div class="new-game-btn" @click="newGame = false">Нова Гра</div>
    </div>
    <div v-show="!newGame">
      <div class="cards" v-if="itemsFirst.length === 6 && itemsSecond.length === 6">
        <circle-card :items="itemsFirst"></circle-card>
        <circle-card :items="itemsSecond"></circle-card>
        <select-container @endOfTime="endGame" :items="items"/>
      </div>
      <div class="points">
        <h1>Кількість балів: {{ points }}</h1>
      </div>
    </div>
  </div>
</template>

<script>
	import CircleCard from './CircleCard';
	import SelectContainer from "./SelectContainer";

	export default {
	components: { SelectContainer, CircleCard },
  data() {
		return {
			newGame: true,
			points: 0,
			items: ['git', 'postgres', 'angular', 'sass', 'vue', 'css3',
        'html5', 'react', 'jquery', 'mongodb', 'javascript', 'mysql',
        'nginx', 'node', 'redux', 'stylus', 'webpack', 'typescript'],
      itemsFirst: [],
      itemsSecond: [],
      // itemsFirst: ['angular', 'git', 'postgres', 'sass', 'vue', 'css3'],
			// itemsSecond: ['html5', 'react', 'jquery', 'angular', 'mongodb', 'javascript']
    }
  },
  mounted() {
    this.generateItems();
  },
  methods: {
		shuffle(array) {
			for (let i = array.length - 1; i > 0; i--) {
				const j = Math.floor(Math.random() * (i + 1));
				[array[i], array[j]] = [array[j], array[i]];
			}
			return array;
    },
	  generateItems() {
			let itemsToUse = this.items;
		  const commonItem = itemsToUse[this.generateRandomIndex(itemsToUse)];
		  this.itemsFirst.push(commonItem);
		  this.itemsSecond.push(commonItem);
		  itemsToUse = itemsToUse.filter(item => item !== commonItem);
		  for (let i = 0; i < 5; i++) {
		  	const firstCardItem = itemsToUse[this.generateRandomIndex(itemsToUse)];
			  this.itemsFirst.push(firstCardItem);
			  itemsToUse = itemsToUse.filter(item => item !== firstCardItem);
			  const secondCardItem = itemsToUse[this.generateRandomIndex(itemsToUse)];
			  this.itemsSecond.push(secondCardItem);
			  itemsToUse = itemsToUse.filter(item => item !== secondCardItem);
      }
		  this.itemsFirst = this.shuffle(this.itemsFirst);
		  this.itemsSecond = this.shuffle(this.itemsSecond);
		  console.log(this.items);
    },
    generateRandomIndex(itemsArray) {
			return Math.floor(Math.random() * itemsArray.length);
    },
	  endGame() {
			// alert('Час вийшов! Ваш результат: ' + this.points + 'балів')
    },
    nextCard() {

    }
  },
	};
</script>

<style>
  .new-game-btn {
    cursor: pointer;
    display: inline-block;
    padding: 0.5em 3em;
    border: 0.16em solid #2c3e50;
    margin: 0 0.3em 0.3em 0;
    box-sizing: border-box;
    text-decoration: none;
    text-transform: uppercase;
    font-family: inherit;
    font-weight: 400;
    color: #2c3e50;
    text-align: center;
    font-size: 15px;
    transition: all 0.35s;
  }
  .new-game-btn:hover {
    color: #DDDDDD;
    border-color: #ddd;
  }
  .description {
    padding: 0 20% 0 20%;
  }
  .cards {
    display: flex;
    margin-left: 100px;
  }
  .points {
    margin-left: 150px;
    text-align: left;
  }
</style>
