<script>
  import { T, useTask, useThrelte } from "@threlte/core";
  import { interactivity } from "@threlte/extras";
  import { Spring } from "svelte/motion";

  interactivity();
  const scale = new Spring(1);

  let rotation = $state(0);
  useTask((delta) => {
    rotation += delta;
  });

  const { camera, renderer } = useThrelte();
</script>

<T.Mesh
  position.y={1}
  rotation.y={rotation}
  scale={scale.current}
  onpointerenter={() => {
    scale.target = 1.5;
  }}
  onpointerleave={() => {
    scale.target = 1;
  }}
  castShadow
>
  <T.BoxGeometry args={[1, 2, 1]} />
  <T.MeshBasicMaterial color="hotpink" />
  <T.MeshStandardMaterial color="hotpink" />
</T.Mesh>
