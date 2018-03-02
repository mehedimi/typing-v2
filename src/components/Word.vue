<template>
	<span class="word" :class="word.status">{{ word.name }} </span>
</template>
<script>
	export default{
		props: ['word']
	}
</script>

<style lang="scss">
	.word{
		color: #fff;
		padding: 10px;
		display: inline-block;
		margin: 10px 0;
		&.initial{
			//background-color: #2d3436;
		}
		&.warning{
			background-color: #f39c12;
		}
		&.wrong{
			background-color: #b71540;
		}
		&.correct{
			background-color: #3498db;
		}
		&.complete{
			background-color: #1abc9c;	
		}
	}
</style>