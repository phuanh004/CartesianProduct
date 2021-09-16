<script lang="ts">
  let inputA = "1,2";

  type MathSet = Array<string | number>;
  let setA: MathSet = [];
  let power_set: Array<MathSet> = [];

  const empty_products = () => {
    power_set.length = 0;
  };

  const generator = function* (set, map = (value: number | string) => value) {
    yield map([]);

    const magnitude = Math.pow(2, set.length);
    for (let c = 1; c < magnitude; c++) {
      yield map(
        set.filter(
          (value: number | string, index: number) => Math.pow(2, index) & c
        )
      );
    }
  };

  const onInputSet = (input_value: string) => {
    if (!input_value) {
      empty_products();
      return;
    }

    setA = [];
    setA = input_value.split(",");

    empty_products();
    for (const subset of generator(setA)) {
      power_set = [...power_set, [subset]];
    }
  };
</script>

<div class="product">
  <div class="set_input_section">
    <label for="setA">Set A = </label>
    {"{ "}<input
      id="setA"
      name="setA"
      type="text"
      bind:value={inputA}
      on:input={onInputSet(inputA)}
    />{" }"}
  </div>

  <div class="result">
    P(A) =
    {#each power_set as product}
      {"{"} {product} {"} "}
    {/each}
  </div>
</div>

<style>
</style>
