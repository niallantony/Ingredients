<script>
  let { team, ingredientCount } = $props();
  import { countable, uncountable } from "$lib/ingredients.json";
  import Item from "./Item.svelte";

  let teamIngredients = $state([]);
  let ingredientsFound = $state(false);

  function getRandomIndex(array) {
    return Math.floor(Math.random() * array.length);
  }

  function getIngredients() {
    let isCountable = true;
    while (teamIngredients.length < ingredientCount) {
      let index = isCountable
        ? getRandomIndex(countable)
        : getRandomIndex(uncountable);
      const item = isCountable ? countable[index] : uncountable[index];
      const same = teamIngredients.filter(
        (inTeam) => inTeam.ingredient === item.ingredient,
      );
      if (same.length) continue;
      teamIngredients.push(item);
      isCountable = isCountable ? false : true;
      ingredientsFound = true;
    }
  }
</script>

<div class="team">
  <h2 class="trade-winds-regular">Team {team}</h2>
  {#if ingredientsFound}
    <div class="ingredientFrame">
      {#each teamIngredients as item}
        <Item {item} />
      {/each}
    </div>
  {:else}
    <button class="trade-winds-regular" onclick={getIngredients}
      >Get Ingredients</button
    >
  {/if}
</div>

<style>
  h2 {
    text-align: center;
  }

  .team {
    flex-grow: 0;
    flex-shrink: 0;
    width: 26rem;
    margin: 2rem;
    border: solid 1px black;
    padding: 1rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    box-shadow: 5px 5px;
  }

  .ingredientFrame {
    display: grid;
    width: 24rem;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 1rem;
    justify-items: center;
  }
</style>
