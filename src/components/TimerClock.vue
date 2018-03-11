<template>
	<div class="clock">
		
	</div>
</template>

<script>
	//import moment from 'moment'

	export default {
		data(){
			return {
				timer: null
			}
		},
		mounted(){
			this.$eventHub.$on('typingStarted', () =>{
				this.timerStart()
			})
		},
		methods: {
			timerStart(){
				this.timer = setTimeout(() => {

				}, 1000)
			}
		}
	}
</script>
<style lang="scss">
	
</style>