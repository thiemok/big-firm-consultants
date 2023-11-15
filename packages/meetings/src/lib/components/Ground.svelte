<script lang="ts">
	import { T } from '@threlte/core';
	import { AutoColliders } from '@threlte/rapier';
	import type { ColorRepresentation } from 'three';
	import type { Vector3Array } from '$lib/utils/types';
	export let position: Vector3Array | undefined;
	export let color: ColorRepresentation;
</script>

<T.Group {position}>
	<AutoColliders shape="cuboid">
		<T.Mesh receiveShadow>
			<T.BoxGeometry args={[10, 1, 10]} />
			<T.MeshStandardMaterial {color} />
		</T.Mesh>
	</AutoColliders>
</T.Group>
