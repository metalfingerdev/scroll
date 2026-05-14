<script>
  import { T, useTask, useThrelte } from "@threlte/core";
  // import { OrbitControls } from "@threlte/extras";
  import { Vector3 } from "three";

  import { reel } from "./film.svelte";
  import { center } from "./actors/donut.config.js";

  const target = new Vector3(...center);
  const distance = 80;
  const stepsPerUnit = 0.001;

  let angle = $derived(reel.length * stepsPerUnit);
  let abscissa = $derived(target.x + distance * Math.sin(angle));
  let ordinate = 40;
  let applicate = $derived(target.z + distance * Math.cos(angle));

  // let abscissa = $derived(0 + reel.length * 0.02); // negative x
  // let ordinate = $derived(40 + reel.length * -0.02); // positive y
  // let applicate = $derived(80 + reel.length * 0); // z unchanged

  const { camera } = useThrelte();
  useTask(() => {
    camera.current.position.set(abscissa, ordinate, applicate);
    camera.current.lookAt(target);
  });
</script>

<T.PerspectiveCamera makeDefault fov={50} />

<!-- <OrbitControls target={[0, 20, 0]} enableDamping enabled={!reel.pause} /> -->
