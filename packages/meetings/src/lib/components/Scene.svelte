<script lang="ts">
	import { T, useFrame } from '@threlte/core';
	import { interactivity } from '@threlte/extras';
	import { spring } from 'svelte/motion';
	import Ground from '$lib/components/Ground.svelte';
	import { Debug } from '@threlte/rapier';
	import Emitter from '$lib/components/Emitter.svelte';

	interactivity();
	const scale = spring(1);

	let rotation = 0;
	useFrame((state, delta) => {
		rotation += delta;
	});
</script>

<T.PerspectiveCamera
	makeDefault
	position={[10, 10, 10]}
	on:create={({ ref }) => {
		ref.lookAt(0, 1, 0);
	}}
/>

<T.DirectionalLight
	position={[0, 10, 10]}
	castShadow
/>

<T.GridHelper args={[50]} />
<Debug />

<T.Mesh
	position.y={1}
	scale={$scale}
	on:pointerenter={() => scale.set(1.5)}
	on:pointerleave={() => scale.set(1)}
	rotation.y={rotation}
	castShadow
>
	<T.BoxGeometry args={[1, 2, 1]} />
	<T.MeshStandardMaterial color="hotpink" />
</T.Mesh>

<Ground
	position={[0, -0.5, 0]}
	color="white"
/>
<Emitter />
