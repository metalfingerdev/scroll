<script>
  import { T } from "@threlte/core";
  import { BackSide } from "three";
</script>

<T.Mesh position={[0, 0, 0]}>
  <T.SphereGeometry args={[400, 20, 20]} />
  <T.MeshBasicMaterial color="#050816" side={BackSide} />
</T.Mesh>
