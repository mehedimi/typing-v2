<template>
	<div class="container">
		<div class="text-content">
			<Word v-for="word in words" :word="word"/>
		</div>
	</div>
</template>

<script>
	import Word from './Word.vue'

	export default {
		components: { Word },
		data(){
			return {
				words: [] 
			}
		},
		mounted(){
			this.words = 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Animi, commodi! Sed eveniet earum dolor saepe ut provident facilis quidem obcaecati nobis quod, autem. Consequatur aliquam fuga possimus tempore. Non, sint.'.split(' ')
		}
	}
</script>

<style lang="scss">
	.text-content{
		border: 1px solid #00a8ff;
		padding: 10px;
		line-height: 35px;
		font-size: 20px;
		font-family: Operator Mono Light;
		color: #7f8fa6
	}
</style>