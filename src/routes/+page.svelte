<script>
  import TeamFrame from "./TeamFrame.svelte";

  let teamCount = $state(1);
  let ingredientCount = $state(6);
  let teams = $state([]);

  function getTeams() {
    teams.length = 0;
    for (let i = 0; i < teamCount; i++) {
      teams.push(i + 1);
    }
  }
</script>

<div class="content">
  <h1 class="trade-winds-regular">Culinary English Class Wars</h1>
  <div class="optionframe">
    <div class="options">
      <label for="teamNumber"
        >Number of Teams:
        <input
          id="teamNumber"
          type="number"
          bind:value={teamCount}
          min="1"
          max="10"
        />
      </label>
      <label for="teamNumber"
        >Number of Ingredients:
        <input
          id="teamNumber"
          type="number"
          bind:value={ingredientCount}
          min="1"
          max="10"
        />
      </label>
    </div>
    <button onclick={getTeams} class="trade-winds-regular">Get Teams</button>
  </div>
  <div class="teamframe">
    {#each teams as team}
      <TeamFrame {team} {ingredientCount} />
    {/each}
  </div>
</div>

<style>
  :root {
    font-family: "Staatliches", sans-serif;
    font-weight: 400;
    font-style: normal;
  }

  .optionframe {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 1rem;
    width: fit-content;
    border: solid 1px black;
    box-shadow: 5px 5px;
  }
  .optionframe label {
    font-size: x-large;
    line-height: 3rem;
    height: 3rem;
    margin-right: 1rem;
  }
  .optionframe input {
    padding: 5px;
    border: solid 1px black;
    margin: 1rem;
    transform: translateY(-5px);
  }
  :global(button) {
    background-color: white;
    padding: 10px;
    font-size: large;
    border: solid 1px black;
    margin: 1rem;
    box-shadow: 5px 5px;
  }
  .teamframe {
    width: 100svw;
    flex-wrap: wrap;
    display: flex;
    justify-items: center;
    gap: 2rem;
    padding: 2rem;
  }
  .content {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  :global(.trade-winds-regular) {
    font-family: "Trade Winds", system-ui;
    font-weight: 400;
    font-style: normal;
  }
</style>
