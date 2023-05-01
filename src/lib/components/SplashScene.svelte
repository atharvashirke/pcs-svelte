<script>
    import { T, useFrame } from '@threlte/core'
    import { Environment, interactivity, GLTF, OrbitControls, useGltf } from '@threlte/extras'
    import { spring } from 'svelte/motion' 

    const gltf = useGltf('/whiteHouse/scene.gltf')

    let rotation = 0
    let envMap
    let material
    useFrame((state, delta) => {
        rotation += delta
    })

    interactivity()
    const scale = spring(1)
</script>

<Environment
  path="/"
  files="splash.png"
  isBackground={true}
  bind:this={envMap}
/>

<T.PerspectiveCamera
  makeDefault
  position={[15, 10, 10]}
  on:create={({ ref }) => {
    ref.lookAt(0, 1, 0)
  }}
>
<OrbitControls autoRotate autoRotateSpeed={1.0} enableDamping enableZoom={false} target={[0, 0, 0]}/>
</T.PerspectiveCamera>

<T.DirectionalLight position={[3, 10, 7]} />
<T.AmbientLight intensity={0.5} />


<T.MeshStandardMaterial metalness={1} roughness={0.5} envMap={envMap} bind:this={material}/>


<GLTF 
  url="/whiteHouse/scene.gltf" 
  position={[0, 1, 0]}
  scale={0.5}
  material={{'whiteHouse': material}}
/>

<T.Mesh
  geometry={$gltf.nodes.geometry}
  material={material}
/>