<script>
	import * as THREE from 'three';
	import * as SC from 'svelte-cubed';

	//import { TextGeometry } from './jsm/geometries/TextGeometry.js';

	let width = 1;
	let height = 1;
	let depth = 1;

	let spin = 0;

	// 	let text = 'three.js',

	// bevelEnabled = true,

	// font = undefined,

	// fontName = 'optimer', // helvetiker, optimer, gentilis, droid sans, droid serif
	// fontWeight = 'bold'; // normal bold

	SC.onFrame(() => {
		spin += 0.01;
	});
</script>

<div class="cancan">
	<div>Oh heeeey!</div>
	<SC.Canvas
		antialias
		background={new THREE.Color('purple')}
		fog={new THREE.FogExp2('green', 0.1)}
		shadows={new THREE.ShadowMaterial(0.5)}
	>
		<SC.Group position={[0, -height / 2, 0]}>
			<SC.Mesh
				geometry={new THREE.PlaneGeometry(50, 50)}
				material={new THREE.MeshStandardMaterial({ color: 'yellow' })}
				rotation={[-Math.PI / 2, 0, 0]}
				receiveShadow
				text={'three.js'}
			/>
			<SC.Primitive
				object={new THREE.GridHelper(50, 50, 'papayawhip', 'papayawhip')}
				position={[0, 0.001, 0]}
			/>
		</SC.Group>

		<SC.Mesh
			geometry={new THREE.BoxGeometry()}
			material={new THREE.MeshStandardMaterial({ color: 0xff3e00 })}
			scale={[width, height, depth]}
			rotation={[0, spin, 0]}
			text={'three.js'}
			castShadow
		/>

		<SC.PerspectiveCamera position={[1, 1, 3]} />
		<SC.OrbitControls enableZoom={false} maxPolarAngle={Math.PI * 0.51} />
		<SC.AmbientLight intensity={0.6} />
		<SC.DirectionalLight intensity={0.6} position={[-2, 3, 2]} shadow={{ mapSize: [2048, 2048] }} />
	</SC.Canvas>
</div>
<div id="info">Description</div>
<div class="controls">
	<label><input type="range" bind:value={width} min={0.1} max={3} step={0.1} /> width</label>
	<label><input type="range" bind:value={height} min={0.1} max={3} step={0.1} /> height</label>
	<label><input type="range" bind:value={depth} min={0.1} max={3} step={0.1} /> depth</label>
	Hiiiii
</div>

<style>
	.cancan {
		max-width: 500px;
	}
	.controls {
		position: absolute;
		left: 2em;
		top: 1em;
	}

	label {
		display: flex;
		width: 60px;
		gap: 0.5em;
		align-items: center;
	}

	input {
		width: 80px;
		margin: 0;
	}
</style>
