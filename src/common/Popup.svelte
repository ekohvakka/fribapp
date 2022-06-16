<script>
  export let game;
  export let teams;
  export let doubles;
</script>

<h2>
  {teams ? "Teams in " : doubles ? "Doubles in " : ""}{game}!
</h2>

<style>
  h2 {
    font-size: 2rem;
    text-align: center;
  }
</style>
