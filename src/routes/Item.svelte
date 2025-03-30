<script>
  let { item } = $props();
</script>

<div class="item">
  <h3>{item.ingredient}</h3>

  <div class="emoji">{item.image}</div>
</div>

<style>
  .emoji {
    text-align: center;
    font-size: xx-large;
  }

  .item {
    border: solid 1px gray;
    width: 100%;
    padding: 1rem;
    box-sizing: border-box;
    height: 10rem;
  }

  h3 {
    text-align: center;
  }
</style>
