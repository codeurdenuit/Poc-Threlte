<script>
import {  PlaneGeometry, MeshBasicMaterial } from 'three'
import { Mesh, useTexture } from '@threlte/core'
export let src

const planeGeo = new PlaneGeometry(10, 10)

const tex = useTexture(src)

</script>

<Mesh
rotation={{ x: 0 }}
geometry={planeGeo}
material={new MeshBasicMaterial({ map:tex })}
/>