<script
	lang="ts"
	context="module"
>
	import { BoxGeometry, MeshStandardMaterial } from 'three';

	const geometry = new BoxGeometry(1, 1, 1);
	const material = new MeshStandardMaterial();
</script>

<script lang="ts">
	import { T } from '@threlte/core';
	import type { Euler, Vector3 } from 'three';
	import type { Vector3Array } from '$lib/utils/types';
	import { Collider, RigidBody } from '@threlte/rapier';

	export let position: Vector3 | undefined;
	export let rotation: Euler | undefined;

	$: rotationCasted = rotation?.toArray() as Vector3Array;
</script>

<T.Group
	position={position?.toArray()}
	rotation={rotationCasted}
>
	<RigidBody type="dynamic">
		<Collider
			contactForceEventThreshold={30}
			restitution={0.4}
			shape={'cuboid'}
			args={[0.5, 0.5, 0.5]}
		/>
		<T.Mesh
			castShadow
			receiveShadow
			{geometry}
			{material}
		/>
	</RigidBody>
</T.Group>
