<template>
  <div class="time">
    <h2><span class="time-left">Залишилось: </span> {{ countDown }} секунд</h2>
  </div>
</template>

<script>
	export default {
		name: 'Counter',
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
			}
		}
	}
</script>

<style lang="scss" scoped>
  @import "../assets/scss/general.scss";
  .time {
    max-width: 100%;
    flex: 0 0 100%;
    display: flex;
    flex-direction: row-reverse;
  }

  .time h2 {
    max-width: 50%;
    flex: 0 0 50%;
    margin: 0;
  }
  @media (max-width: 768px) {
    .time-left {
      display: none;
    }

    .time h2{
      position: absolute;
      top: calc-size-mobile(17);
      right: calc-size-mobile(15);
    }

  }


</style>
