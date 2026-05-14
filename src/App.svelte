<script>
  import { Canvas } from "@threlte/core";
  import { reel } from "./lib/film.svelte.js";

  import Scene from "./Scene.svelte";
</script>

<svelte:window onwheel={(e) => (reel.length -= e.deltaY)} />

<Canvas>
  <Scene />
</Canvas>

<!-- markup -->
<main>
  <div id="scroll" style="transform: translateY({reel.length}px)">
    <p>A Film By</p>
    <h1>Lorem Ipsum</h1>
    <section>
      <h2>Directed by</h2>
      <p>Lorem Ipsum</p>
    </section>
    <section>
      <h2>Produced by</h2>
      <p>Dolor Sit Amet</p>
      <p>Consectetur Adipiscing</p>
    </section>
    <section>
      <h2>Written by</h2>
      <p>Elit Sed Do</p>
    </section>
    <section>
      <h2>Cinematography</h2>
      <p>Eiusmod Tempor</p>
    </section>
    <section>
      <h2>Original Score</h2>
      <p>Incididunt Ut Labore</p>
    </section>
    <section>
      <h2>Visual Effects</h2>
      <p>Veniam Quis Nostrud</p>
      <p>Exercitation Ullamco</p>
    </section>
    <p class="fin">— fin —</p>
  </div>
</main>

<style>
  main {
    position: fixed;
    inset: 0;
    pointer-events: none;
    z-index: 10;

    #scroll {
      display: flex;
      flex-direction: column;
      text-align: center;
      align-items: center;
    }
  }
</style>
