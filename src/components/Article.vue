<template>
	<div class="container">
		<div class="text-content">
			<Word v-for="(word, index) in words" :key="index" :word="word"/>
		</div>
		<TypeInput :correct-word="currentWord"/>
	</div>
</template>

<script>
	import Word from './Word.vue'
	import TypeInput from './TypeInput.vue'
	export default {
		components: { Word, TypeInput },
		data(){
			return {
				words: [],
				currentPosition: 0
			}
		},
		mounted(){
			this.setArticle()
			this.registerEvents()
		},
		methods: {
			setArticle(){
				let words = 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Animi, commodi! Sed eveniet earum dolor saepe ut provident facilis quidem obcaecati nobis quod, autem. Consequatur aliquam fuga possimus tempore. Non, sint.'.split(' ')	
				words.forEach((word) => {
					this.words.push({
						name: word + ' ',
						status: 'initial'
					})
				})
			},
			registerEvents(){
				this.$on('changeTypingPosition', () => {
					this.currentPosition++
				})
				this.$on('updateWordStatus', (status) => {
					this.findWord(this.currentPosition).status = status
				})
			},
			findWord(index){
				return this.words[index]
			}
		},
		computed: {
			currentWord(){
				return this.words[this.currentPosition]
			}
		}
	}
</script>

<style lang="scss">
	.text-content{
		border: 1px solid #00a8ff;
		padding: 10px;
		font-size: 20px;
		font-family: "Operator Mono Bold";
		color: #7f8fa6
	}
</style>