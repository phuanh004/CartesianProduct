<script lang="ts">
  import SetProduct from "./lib/SetProduct.svelte";
  import PowerSet from "./lib/PowerSet.svelte";
</script>

<main>
  <h3 class="title">Cartesian Product of Two Sets</h3>
  <i>(Click inside set A or B then start typing...)</i>
  <div class="set_product">
    <p class="instruction">
      a) Given two finite sets, list all elements in the Cartesian product of
      these two sets.
    </p>
    <SetProduct />
  </div>

  <div class="power_set">
    <p class="instruction">
      b) Given a finite set, list all elements of its power set.
    </p>
    <PowerSet />
  </div>
</main>

<style>
  :root {
    font-family: "Darker Grotesque", sans-serif;
    font-size: x-large;
  }

  h3.title {
    @apply font-bold mt-5 text-6xl;
  }

  .instruction {
    @apply font-bold mt-2 text-2xl;
  }

  main {
    @apply container mx-auto;
  }
</style>
