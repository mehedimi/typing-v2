<template>
	<div class="statistics">
		<div class="widget-parcials">
			asaf
		</div>
		<div class="widget-parcials">
			<TimerClock/>
		</div>
		<div class="widget-parcials">
			WPM
		</div>
	</div>
</template>

<script>
	import TimerClock from './TimerClock'

	export default {
		components: {
			TimerClock
		}
	}
</script>

<style lang="scss">
	.statistics{
		display:flex;
		justify-content: space-around;
		margin: 4em;
	}
</style>