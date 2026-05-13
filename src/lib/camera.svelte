<script>
  import { T, useTask, useThrelte } from "@threlte/core";
  import { Vector3 } from "three";
  // import { OrbitControls } from "@threlte/extras";
  import { reel } from "./film.svelte";

  const TARGET = new Vector3(0, 20, 0);
  const DISTANCE = 80;

  const ordinate = 40;
  const stepsPerUnit = 0.001;

  let angle = $derived(reel.length * stepsPerUnit);
  let abscissa = $derived(TARGET.x + DISTANCE * Math.sin(angle));
  let applicate = $derived(TARGET.z + DISTANCE * Math.cos(angle));

  // let abscissa = $derived(0 + reel.length * 0.02); // negative x
  // let ordinate = $derived(40 + reel.length * -0.02); // positive y
  // let applicate = $derived(80 + reel.length * 0); // z unchanged

  const { camera } = useThrelte();
  useTask(() => {
    camera.current.position.set(abscissa, ordinate, applicate);
    camera.current.lookAt(TARGET);
  });
</script>

<T.PerspectiveCamera makeDefault fov={50} />

<!-- <OrbitControls target={[0, 20, 0]} enableDamping enabled={!reel.pause} /> -->
