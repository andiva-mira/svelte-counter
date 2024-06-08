<script>
  import Team from './Team.svelte';

      //Team Counter
    let teamRed = "Red";
    let teamBlue = "Blue";
    let redScore = 20;
    let blueScore = 20;

    $: redWon = blueScore === 0;
    $: blueWon = redScore === 0;
    $: gameOver = redWon || blueWon;

    function resetScore() {
      redScore = 20;
      blueScore = 20;
    }
</script>

<div class="counter">

  <h1>Counter Game</h1>

  <div class="flex-row">
    <Team gameOver={gameOver} team={teamRed} bind:score={redScore}/>
    <Team gameOver={gameOver} team={teamBlue} bind:score={blueScore} />   
</div>
<div class="mt-20">
  {#if gameOver}
      <p>{blueWon ? teamBlue : teamRed} Team  has won! &#128515;&#128515;&#128515;</p>
      <button on:click={resetScore}> New Game</button>
    {:else}
    <!-- show reset button if start score changes -->
    {#if redScore !== 20 || blueScore !== 20}
      <button class="btn-light" on:click={resetScore}> Reset Game</button>
    {/if}
  {/if}
</div>
</div>

<style>
    .counter {
        max-width: 500px;
        margin: 30px auto;
    }

    .flex-row {
      grid-gap: 20px;
    }

    button {
      width: 100%;
    }
</style>
