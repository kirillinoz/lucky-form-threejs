<template>
	<div class="row">
		<div class="column">
			<Form @changed="onSpeedChanged" @submitted="onSubmit" />
		</div>
		<div class="column">
			<LuckyBlock
				:speed="speed"
				:radius="radius"
				:LBvisible="LBvisible"
				:positionY="positionY"
			/>
		</div>
	</div>
</template>

<script>
import LuckyBlock from './components/LuckyBlock.vue'

import Form from './components/Form.vue'

export default {
	data() {
		return {
			speed: 1,
			radius: 7,
			LBvisible: true,
			positionY: 2,
		}
	},
	components: {
		LuckyBlock,
		Form,
	},
	methods: {
		onSpeedChanged(value) {
			this.speed = value
		},
		onSubmit() {
			const zoomOutInterval = setInterval(() => {
				this.radius += 4
			}, 10)

			setTimeout(() => {
				clearInterval(zoomOutInterval)
				this.speed = 1
				this.LBvisible = false
				zoomOut()
			}, 1000)

			const zoomOut = () => {
				const zoomInInterval = setInterval(() => {
					this.radius -= 4
				}, 9)

				setTimeout(() => {
					clearInterval(zoomInInterval)
					this.radius = 13
				}, 1000)
			}
		},
	},
}
</script>

<style>
html {
	font-size: 16px;
}

* {
	margin: 0;
	padding: 0;
	font-family: 'Poppins', sans-serif;
}
body {
	margin: 0;
	width: 100vw;
	height: 100vh;
	box-sizing: border-box;
}

#app {
	width: 100%;
	height: 100%;
	display: flex;
	justify-content: center;
}
.row {
	display: flex;
	width: 100%;
}
.column {
	flex: 50%;
	display: flex;
	justify-content: center;
	align-items: center;
}

@media only screen and (max-width: 830px) {
	.row {
		margin-top: 2rem;
		flex-direction: column;
	}
}

@media only screen and (max-width: 400px) {
	html {
		font-size: 14px;
	}
}

@media only screen and (max-width: 350px) {
	html {
		font-size: 12px;
	}
}

@media only screen and (max-width: 300px) {
	html {
		font-size: 10px;
	}
}
</style>
