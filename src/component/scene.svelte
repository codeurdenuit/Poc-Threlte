<script>
  import { CircleBufferGeometry, MeshStandardMaterial, BoxBufferGeometry, DoubleSide } from 'three'
  import {AmbientLight, Canvas, DirectionalLight, Group, Mesh, Line, OrbitControls, PerspectiveCamera } from '@threlte/core'
  import Grid from './geometry/grid';
  import Deformer from './Deformer/index.svelte'
  import materialLine from './material/materialLine'
  let scale = 1
  const gridGeo = new Grid(10, 10, 10, 10)
  let image = '/sample.png'
</script>

<div>
  <Canvas>
    <PerspectiveCamera position={{ x: 10, y: 10, z: 10 }} fov={24}>
      <OrbitControls
        maxPolarAngle={Math.PI/2}
        autoRotate={false}
        enableZoom={false}
        target={{ y: 0.5 }}
      />
    </PerspectiveCamera>

    <DirectionalLight shadow position={{ x: 3, y: 10, z: 10 }} />
    <AmbientLight intensity={0.2} />

    <!--<Group>
      <Mesh
        interactive
        on:pointermove={(e) => (console.log(e))}
        position={{ y: 0.5 }}
        scale={{y:scale}}
        castShadow
        geometry={new BoxBufferGeometry(1, 1, 1)}
        material={new MeshStandardMaterial({ color: '#333333' })}
      />
    </Group>-->

    <!--<Mesh
      receiveShadow
      rotation={{ x: -90 * (Math.PI / 180) }}
      geometry={new CircleBufferGeometry(3, 72)}
      material={new MeshStandardMaterial({ side: DoubleSide, color: 'white' })}
    />-->
    <Deformer src={image} />

    <Line
    geometry={gridGeo}
    material={materialLine}
  />

  </Canvas>
</div>

<style>
  div {
    height: 100%;
    width: 100%;
    position: fixed;
  }
</style>