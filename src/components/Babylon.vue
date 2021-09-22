<template>
	<div>
		<canvas id='renderCanvas'></canvas>
	</div>
</template>

<script>
	import * as BABYLON from '@/assets/vendors/babylon.min.js';

	export default {
		name: 'Babylon',

		mounted: function () {
			
			const createScene = () => {
				const scene = new BABYLON.Scene(engine);
				const camera = new BABYLON.ArcRotateCamera('camera', -Math.PI / 2, Math.PI / 2.5, 3, new BABYLON.Vector3(0, 0, 0));
				camera.attachControl(canvas, true);
				const light = new BABYLON.HemisphericLight('light', new BABYLON.Vector3(0, 1, 0));
				const box = BABYLON.MeshBuilder.CreateBox('box', {});

				return scene;
			}
			
			const canvas = document.getElementById('renderCanvas');
			const engine = new BABYLON.Engine(canvas, true);
			const scene = createScene();

			engine.runRenderLoop(function() {
				scene.render();
			});

			window.addEventListener('resize', function () {
				engine.resize();
			});
		},

		methods: {},
	};
</script>

<style scoped>
	canvas {
		width: 100%;
		position: fixed;
		height: 100vh;
	}
</style>