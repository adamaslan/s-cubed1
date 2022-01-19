<script>
	import * as THREE from 'three';
	import * as SC from 'svelte-cubed';
</script>
//cute and red globe! just need text!
<SC.Canvas antialias background={new THREE.Color('papayawhip')}>
	<SC.Mesh
		geometry={new THREE.BoxGeometry()}
		material={new THREE.MeshStandardMaterial({ color: 0xff3e00 })}
	/>
<SC.AmbientLight intensity={0.6} />
	<SC.DirectionalLight intensity={0.6} position={[-2, 3, 2]} />
	<SC.PerspectiveCamera position={[2, 1, 1]} />
	<SC.OrbitControls enableZoom={false} />
</SC.Canvas>
