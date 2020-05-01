<script>
	import { onMount } from 'svelte';
	import * as THREE from 'three';

	onMount(() => {
		const mainEl = document.body.querySelector('main');
		var scene = new THREE.Scene();
		var camera = new THREE.PerspectiveCamera( 75, window.innerWidth/window.innerHeight, 0.1, 1000 );

		var renderer = new THREE.WebGLRenderer();
		renderer.setSize( window.innerWidth, window.innerHeight );
		mainEl.appendChild( renderer.domElement );

		var geometry = new THREE.BoxGeometry();
		var material = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );
		var cube = new THREE.Mesh( geometry, material );
		scene.add( cube );

		camera.position.z = 2;

		var animate = function () {
			requestAnimationFrame( animate );

			cube.rotation.x += 0.01;
			cube.rotation.y += 0.01;

			renderer.render( scene, camera );
		};

		animate();
	});
</script>

<main>

</main>

<style>
	main {
		margin: 0 auto;
	}

	canvas { 
		width: 100%; 
		height: 100%;
		display: block;
	}
</style>