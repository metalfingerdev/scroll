<script>
  import { T } from "@threlte/core";
  import { MathUtils } from "three";

  // Cube ( 200 = side )
  //  const stars = Array.from({ length: count }, () => ({
  //    x: MathUtils.randFloatSpread(200),
  //    y: MathUtils.randFloatSpread(200),
  //    z: MathUtils.randFloatSpread(200),
  //  }));

  const count = 420;
  const radius = 400;
  const height = 450;
  const rocheLimit = 200;

  function genesis() {
    while (true) {
      // Cylinder ( 400 = height, diameter )
      const r = Math.sqrt(Math.random()) * radius;
      const theta = Math.random() * Math.PI * 2;
      const h = MathUtils.randFloatSpread(height);

      const x = r * Math.cos(theta);
      const y = h;
      const z = r * Math.sin(theta);

      if (x * x + y * y + z * z > rocheLimit ** 2) {
        return { x, y, z };
      }
    }
  }
  const stars = Array.from({ length: count }, genesis);
</script>

{#each stars as star}
  <T.Mesh position={[star.x, star.y, star.z]}>
    <T.SphereGeometry args={[0.5, 8, 8]} />
    <T.MeshStandardMaterial color="white" />
  </T.Mesh>
{/each}
