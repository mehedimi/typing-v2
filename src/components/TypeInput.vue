<template>
	<div class="type-area">
		<div class="type-input">
			<input v-model="word" @keyup="typing" type="text" class="input" placeholder="Start typing....">
		</div>
	</div>
</template>

<script>
	export default {
		props: [
			'correctWord'
		],
		data(){
			return {
				word: '',
				typeStarted: false
			}
		},
		mounted(){
			this.$parent.$on('typingFinished', () => {
				this.typeStarted = false
			})
		},
		methods: {
			typing(e){
				if(!this.typeStarted){
					this.typeStarted = true
				}
				let status = this.validateWord(this.correctWord.name, this.word)
				if(e.keyCode == 32){
					this.$parent.$emit('updateWordStatus', status ? 'complete' : 'wrong')
					this.$parent.$emit('changeTypingPosition')
					this.word = ''
					return
				}
				
				this.$parent.$emit('updateWordStatus', status ? 'correct' : 'warning');
			},
			changeWord(){
				this.$parent.$emit('changeTypingPosition')
				this.word = ''
				let status = this.validateWord(this.correctWord.name + ' ', this.word)
				this.$parent.$emit('updateWordStatus', status ? 'correct' : 'wrong');
			},
			validateWord(correctWord, typingWord){
				let regex = `^${typingWord}.*$`
				return new RegExp(regex).test(correctWord)
			},
			
		},
		watch: {
			typeStarted(status){
				this.$parent.$emit('changeTypingStatus', status)
			}
		}
	}
</script>
<style lang="scss">
	.type-area{
		padding: 20px;
		text-align: center;
		.type-input{
			max-width: 450px;
			margin: auto
		}
		.input{
			padding:15px;
			width: 100%;
			box-sizing: border-box;
			border: 1px solid #ddd;
			font-size: 19px;
			transition: 0.6s;
			&:focus{
				outline: none;
				border-color: #00a8ff;
				box-shadow: 0px 0px 0px 4px #00A8FF
			} 
		}
	}
</style>