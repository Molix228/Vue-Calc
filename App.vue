<template>
  <div id="app">
		<div class="grid">
			<input @keyup.enter="calc()" type="text" v-model="result" placeholder="0">
			<button @click="input(num)" class="cell num" v-for="num in numbers">{{ num }}</button>
			<button @click="input(op)" class="cell op" v-for="op in operations">{{ op }}</button>
			<button @click="reset()" class="cell op">R</button>
			<button @click="calc()" class="cell op">=</button>
		</div>
	</div>
</template>

<script>


export default {
  data() {
		return {
			result: '',
			numbers: [1,2,3,4,5,6,7,8,9,0],
			operations: ['+', '-', '*', '/']
		}
	},
	methods: {
		input: function(char) {
			this.result = this.result.toString();
			this.result+=char;

		},
		reset: function () {
			this.result = '';
		},
		calc: function () {
			this.result = eval(this.result);
		}
	}
}


</script>

<style scoped>
	* {
		font-family: 'Gilroy', sans-serif;
		transition: 0.3s all;
		font-weight: 600;
	}
	#app {
		width: 200px;
		box-shadow: 0 3px 15px grey;
		position: relative;
	}
	input[type="text"] {
		width: 100%;
		border: 0;
		color: #243849;
		font-size: 18px;
		padding: 5px 5px;
		text-align: right;
	}
	input[type="text"]:hover {
		height: 40px;
	}
	.grid {
		display: flex;
		flex-wrap: wrap;
		justify-content: space-around;
	}
	.cell {
		flex: 33%;
		height: 50px;
		font-size: 18px;
		border: none;
	}
	.num {
		background-color: #243849;
		color: #fff;
		font-weight: 400;
	}
	.cell:hover {
		background-color: #182530;
	}
	.op {
		background-color: #ff9900;
		color: #243849;
	}
	.op:hover{
		color: #fff;
	}

</style>
