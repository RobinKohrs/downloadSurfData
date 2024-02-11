<script>
  let url =
    "https://services.surfline.com/kbyg/spots/forecasts/wave?spotId=5842041f4e65fad6a7708e80&days=5&intervalHours=1&cacheEnabled=true&units[swellHeight]=M&units[waveHeight]=M";

  let data;
  async function fetchData() {
    let rawResponse = await fetch(url, {
      mode: "no-cors",
    });
    let jsonResponse = await rawResponse.json();
    data = jsonResponse;
  }
</script>

<main>
  <button on:click={fetchData}>Fetch data</button>
  {#if data}
    {JSON.stringify(data)}
  {/if}
</main>

<style>
  main {
    height: 100vh;
    width: 100vw;
    display: grid;
    justify-content: center;
    align-items: start;
  }

  button {
    padding: 1rem 2rem;
    justify-self: center;
  }
</style>
