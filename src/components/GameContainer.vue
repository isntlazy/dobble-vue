<template>
  <div>
    <div class="cards">
      <circle-card :items="shuffle(items)"></circle-card>
      <circle-card :items="shuffle(items2)"></circle-card>
      <div>
        <h2>Залишилось: 15 секунд</h2>
        <h4>Виберіть спільний елемент:</h4>
      </div>
    </div>
  </div>
</template>

<script>
import CircleCard from './CircleCard';
export default {
	components: { CircleCard },
  data() {
		return {
			items: ['angular', 'git', 'postgres', 'sass', 'vue', 'css3'],
			items2: ['html5', 'react', 'jquery', 'angular', 'mongodb', 'javascript']
    }
  },
  methods: {
		shuffle(array) {
			for (let i = array.length - 1; i > 0; i--) {
				const j = Math.floor(Math.random() * (i + 1));
				[array[i], array[j]] = [array[j], array[i]];
			}
			return array;
    }
  }
};
</script>

<style>
  .cards {
    display: flex;
    margin-left: 200px;
  }
</style>
