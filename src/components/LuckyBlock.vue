<template>
	<Renderer
		ref="renderer"
		antialias
		:orbit-ctrl="{ enableDamping: true }"
		:alpha="true"
		:resize="true"
	>
		<Camera
			:position="{
				x: radius * Math.cos(t),
				y: positionY,
				z: radius * Math.sin(t),
			}"
		/>
		<Scene ref="scene">
			<PointLight :position="{ x: lightIntensity, y: 0, z: 0 }" />
			<PointLight :position="{ x: -lightIntensity, y: 0, z: 0 }" />
			<PointLight :position="{ x: 0, y: lightIntensity, z: 0 }" />
			<PointLight :position="{ x: 0, y: -lightIntensity, z: 0 }" />
			<PointLight :position="{ x: 0, y: 0, z: lightIntensity }" />
			<PointLight :position="{ x: 0, y: 0, z: -lightIntensity }" />
			<GltfModel src="../../assets/LuckyBlock.glb" :visible="LBvisible" />
			<GltfModel
				src="../../assets/Cake.glb"
				:visible="!LBvisible"
				:position="{ x: 0, y: -3.5, z: 0 }"
			/>
		</Scene>
	</Renderer>
</template>

<script>
export default {
	data() {
		return {
			t: 0.2,
			lightIntensity: 100,
		}
	},
	props: {
		speed: Number,
		radius: Number,
		LBvisible: Boolean,
		positionY: Number,
	},
	mounted() {
		setInterval(() => {
			this.t += this.speed * 0.01
		}, 10)
	},
}
</script>

<style>
canvas {
	display: block;
	width: 100%;
	height: 100%;
}
</style>

<!--<Box ref="box" :rotation="{ y: Math.PI / 4, z: Math.PI / 4 }">
				<LambertMaterial />
			</Box>-->
