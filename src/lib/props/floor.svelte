<script>
  import { T } from "@threlte/core";
</script>

<T.Mesh rotation.x={-Math.PI / 2} receiveShadow>
  <T.CircleGeometry args={[200, 40]} />
  <T.MeshStandardMaterial color="white" />
</T.Mesh>
