<script lang="ts">
  let inputA = "1,2";
  let inputB = "3,4";

  type MathSet = Array<string | number>;
  let setA: MathSet = [1, 2];
  let setB: MathSet = [3, 4];
  let cartesian_product_list: Array<MathSet> = [];

  const cartesian_product = () => {
    setA.forEach((elementInA) => {
      setB.forEach((elementInB) => {
        cartesian_product_list = [
          ...cartesian_product_list,
          [elementInA, elementInB],
        ];
      });
    });
  };

  const empty_products = () => {
    cartesian_product_list.length = 0;
  };

  const empty_set = (setName: string) => {
    switch (setName) {
      case "a":
        setA = [];
        break;

      case "b":
        setB = [];
        break;

      default:
        break;
    }
  };

  const onInputSet = (setName: string, input_value: string) => {
    if (!input_value) {
      empty_set(setName);
      empty_products();
      return;
    }

    switch (setName) {
      case "a":
        setA = [];
        setA = input_value.split(",");
        break;

      case "b":
        setB = [];
        setB = input_value.split(",");
        break;

      default:
        break;
    }

    empty_products();
    cartesian_product();
  };

  cartesian_product();
</script>

<div class="product">
  <div class="set_input_section">
    <label for="setA">Set A = </label>
    {"{ "}<input
      id="setA"
      name="setA"
      type="text"
      bind:value={inputA}
      on:input={onInputSet("a", inputA)}
    />{" }"}
  </div>

  <div class="set_input_section">
    <label for="setA">Set B = </label>
    {"{ "}<input
      id="setB"
      name="setB"
      type="text"
      bind:value={inputB}
      on:input={onInputSet("b", inputB)}
    />{" }"}
  </div>

  <div class="result">
    A x B = {"{ "}
    {#each cartesian_product_list as product}
      {"( "} {product} {" ) "}
    {/each}

    {" }"}
  </div>
</div>

<style>
</style>
