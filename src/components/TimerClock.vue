<template>
	<div class="clock">
		<h1>{{ timerString }}</h1>
	</div>
</template>

<script>
	import moment from 'moment'

	export default {
		data(){
			return {
				timer: null,
				timerString: '00 : 00'
			}
		},
		mounted(){
			this.$eventHub.$on('typingStarted', () =>{
				this.timerStart()
			})
		},
		methods: {
			timerStart(){
				let typeStartTime = moment().unix()
				let typeEndTime = moment().add(0.3, 'minutes').unix()
				let diffTime = typeEndTime - typeStartTime
				let duration = moment.duration(diffTime * 1000, 'milliseconds')
				this.timer = setInterval(() => {
					if(duration.asMilliseconds() === 0){
						return this.finishTimer()
					}
					duration = moment.duration(duration.asMilliseconds() - 1000)
					this.timerString = moment(duration.asMilliseconds()).format('mm : ss')
				}, 1000)
			},
			finishTimer(){
				clearInterval(this.timer)
			}
		}
	}
</script>
<style lang="scss">
	
</style>