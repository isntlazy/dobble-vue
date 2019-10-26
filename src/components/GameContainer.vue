<template>
  <div>
    <div class="new-game" v-if="newGame">
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
      <div class="new-game-btn" @click="startGame">Нова Гра</div>
    </div>
    <div v-else>
      <div class="cards" v-if="itemsFirst.length === 6 && itemsSecond.length === 6 && !gameOver">
        <counter @endOfTime="endGame" ></counter>
        <div class="circle-container">
          <circle-card :items="itemsFirst"></circle-card>
          <circle-card :items="itemsSecond"></circle-card>
        </div>
        <select-container @nextCard="nextCard" :common-item="commonItem" :items="items"/>
      </div>
      <div v-if="gameOver">
        <h3>Кінець гри! Ваш результат: {{ points }} балів(и)</h3>
        <div class="new-game-btn" @click="startGame">Нова Гра</div>
      </div>
      <div class="points" v-show="!gameOver">
        <h1>Кількість балів: {{ points }}</h1>
      </div>
    </div>
  </div>
</template>

<script>
	import CircleCard from './CircleCard';
	import SelectContainer from "./SelectContainer";
	import Counter from "./Counter";

	export default {
	components: { SelectContainer, CircleCard, Counter },
  data() {
		return {
			newGame: true,
      gameOver: false,
			points: 0,
			items: ['git', 'postgres', 'angular', 'sass', 'vue', 'css3',
        'html5', 'react', 'jquery', 'mongodb', 'javascript', 'mysql',
        'nginx', 'node', 'redux', 'stylus', 'webpack', 'typescript'],
      commonItem: null,
      itemsFirst: [],
      itemsSecond: [],
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
		  this.itemsFirst = [];
		  this.itemsSecond = [];
		  const commonItem = itemsToUse[this.generateRandomIndex(itemsToUse)];
		  this.itemsFirst.push(commonItem);
		  this.itemsSecond.push(commonItem);
		  this.commonItem = commonItem;
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
    },
    generateRandomIndex(itemsArray) {
			return Math.floor(Math.random() * itemsArray.length);
    },
    startGame() {
			this.points = 0;
	    this.gameOver = false;
			this.newGame = false;
    },
	  endGame() {
			this.gameOver = true;
    },
    nextCard() {
      this.points++;
      this.generateItems();
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
    font-size: calc(15 / 1680 * 100vw);
    transition: all 0.35s;
  }
  .new-game-btn:hover {
    color: #ddd;
    border-color: #ddd;
  }
  .description {
    padding: 0 20% 0 20%;
  }
  .circle-container {
    max-width: 50%;
    flex: 0 0 50%;
    display: flex;
    justify-content: space-around;
  }

  .cards {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
  }
  .points {
    margin-left: calc(90 / 1680 * 100vw);
    text-align: left;
  }
  @media (max-width: 768px) {
    .circle-container {
      max-width: 100%;
      flex: 0 0 100%;
      justify-content: space-between;
    }
    h2 {
      font-size: calc(20 / 375 * 100vw);
    }
  }

  @media (max-width: 480px) {
    .circle-container {
      flex-direction: column;
      align-items: center;
    }

    .points {
      margin-left: 0;
    }
  }
</style>
