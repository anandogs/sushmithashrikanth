<script>
	// @ts-nocheck
    import { onMount } from 'svelte';

	let canvasSelector;
	import * as THREE from 'three';
    onMount(async () => {
	const scene = new THREE.Scene();
	const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
	const renderer = new THREE.WebGLRenderer({
		canvas: canvasSelector,
        alpha: true,
	});
    
	renderer.setPixelRatio(window.devicePixelRatio);
	renderer.setSize(window.innerWidth*.3, window.innerHeight*.3);

	// moves the camera backwards - otherwise it is in the middle of the object
	camera.position.setZ(50);
	camera.position.setY(0);
	camera.position.setX(0);


	renderer.render(scene, camera);

	const geometry = new THREE.TorusKnotGeometry(10, 3, 100, 16);
	const material = new THREE.MeshStandardMaterial({
		color: 0x1875A4,
		roughness: 0.5,
		metalness: .5,
		alphaTest: 0,
	});
	const capsule = new THREE.Mesh(geometry, material);
	scene.add(capsule);


	const pointLight = new THREE.PointLight(0xffffff);
	pointLight.position.set(5, 5, 5);
	const ambientLight = new THREE.AmbientLight(0xffffff);
	scene.add(pointLight, ambientLight);

	function animate() {
		requestAnimationFrame(animate);
		capsule.rotation.x += 0.02;
		capsule.rotation.y += 0.005;
		capsule.rotation.z += 0.01;

		renderer.render(scene, camera);
	}

	animate();
})
</script>
<div class="flex justify-center">
<p class="text-white"></p>
	<canvas bind:this={canvasSelector} />
</div>