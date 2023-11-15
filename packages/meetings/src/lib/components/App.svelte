<script lang="ts">
	import { Canvas } from '@threlte/core';
	import Scene from './Scene.svelte';
	import { World } from '@threlte/rapier';
	import { HTML } from '@threlte/extras';
</script>

<Canvas>
	<World>
		<Scene />
		<HTML
			slot="fallback"
			transform
		>
			<p>
				It seems your browser<br />
				doesn't support WASM.<br />
				I'm sorry.
			</p>
		</HTML>
	</World>
</Canvas>
