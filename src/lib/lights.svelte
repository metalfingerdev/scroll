<script>
  import { T } from "@threlte/core";
</script>

<T.DirectionalLight
  args={[0xffffff]}
  intensity={1}
  position={[0, 10, 20]}
  castShadow
  shadow.mapSize={[2048, 2048]}
  shadow.bias={-0.0005}
  shadow.normalBias={0.05}
  // Hubble sphere from light source
  shadow.camera.left={-50}
  shadow.camera.right={50}
  shadow.camera.top={50}
  shadow.camera.bottom={-50}
  shadow.camera.near={0.1}
  shadow.camera.far={100}
/>

<T.AmbientLight intensity={0.2} />
