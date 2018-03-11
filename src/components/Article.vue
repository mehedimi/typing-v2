<template>
	<div class="container">
		<div class="text-content">
			<Word v-for="(word, index) in words" :position="index" :key="index" :word="word"/>
		</div>
		<TypeInput :correct-word="currentWord"/>
		<Statistics/>
	</div>
</template>

<script>
	import Word from './Word.vue'
	import TypeInput from './TypeInput.vue'
	import Statistics from './Statistics'

	export default {
		components: { Word, TypeInput, Statistics },
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
				let words = 'Lorem ipsum dolor sit amet'.split(' ')	
				words.forEach((word) => {
					this.words.push({
						name: word + ' ',
						status: 'initial'
					})
				})
			},
			registerEvents(){
				this.$on('changeTypingPosition', () => {
					if((this.words.length - 1) == this.currentPosition){
						this.typingFinish()
						return;
					}
					this.currentPosition++
				})
				this.$on('updateWordStatus', (status) => {
					this.findWord(this.currentPosition).status = status
				})
			},
			findWord(index){
				return this.words[index]
			},
			typingFinish(){
				this.$emit('typingFinished')
			}
		},
		computed: {
			currentWord(){
				return this.words[this.currentPosition]
			}
		},
		watch: {
			currentPosition(index){
				this.words[index].status = 'correct'
				this.$emit('currentPosition', index)
			}
		}
	}
</script>

<style lang="scss">
	.text-content{
		border: 1px solid #00a8ff;
		padding: 10px;
		font-size: 20px;
		color: #7f8fa6
	}
</style>