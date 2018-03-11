<template>
	<span class="word" :class="[word.status, (isTypingStart && currentIndex == position) ? 'typing' : '']">{{ word.name }} </span>
</template>
<script>
	export default {
		props: ['word', 'position'],

		data(){
			return {
				isTypingStart: false,
				currentIndex: 0
			}
		},
		mounted(){
			this.$parent.$on('changeTypingStatus', (status) => {
				this.isTypingStart = status
			})
			this.$parent.$on('currentPosition', (indexPosition) => {
				this.currentIndex = indexPosition
			})
		}
	}
</script>

<style lang="scss">
	.word{
		color: #fff;
		display: inline-block;
		margin: 5px;
		color: #353b48;
		border-bottom: 2px solid transparent;
		&.initial{
			opacity: 0.8;
		}
		&.warning{
			color: #f39c12;
		}
		&.wrong{
			color: #b71540;
		}
		&.correct{
			color: #3498db;
		}
		&.complete{
			color: #1abc9c;	
		}
		&.typing{
			border-color: #000;
			animation: pulseBorder 0.7s infinite;
		}
	}
	@keyframes pulseBorder {
		0%{
			border-color: #fff;
		}
		50%{
			border-color: #000
		}
		100%{
			border-color: #fff
		}
	}
</style>