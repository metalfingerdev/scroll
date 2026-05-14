<script>
  import { T, useTask } from "@threlte/core";
  import { reel } from "../film.svelte";
  import { interactivity } from "@threlte/extras";
  import { center } from "./donut.config.js";
  interactivity();

  let rotation = $state(0);
  useTask((delta) => {
    if (reel.pause) return;

    rotation += delta * reel.RPS;
  });
</script>

<T.Mesh
  position.x={center[0]}
  position.y={center[1]}
  position.z={center[2]}
  rotation.y={rotation * 2}
  rotation.x={rotation}
  rotation.z={rotation / 2}
  castShadow
>
  <T.TorusGeometry args={[10, 3, 16, 100]} />
  <T.MeshStandardMaterial color="hotpink" />
</T.Mesh>
