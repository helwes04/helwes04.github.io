<script>
  let clicks = 0;
  let multiplier = 1;
  let workers = [];
  let worker_multiplier = 1;

  let upgrades = [
    { cost: 15, name: "Adder", multiplier: 1, worker: 0 },
    { cost: 5, name: "Worker", multiplier: 0, worker: 1 },
  ];

  function increment() {
    clicks = clicks + multiplier;
    console.log("click" + clicks);
  }
</script>

<details>
<summary>Just saying</summary>
<p>Star Wars 4-6 is btw the best Movie Triology ever just saying </p>
</details>
<marquee behavior="slide"scrollamount="6"scrolldelay="20"truespeed>We provide fresh cookies betwene 09:50am - 12:15pm but you have to make them yourself</marquee>

<h1>Ett litet bageri</h1>

<article>
  <header>
    <div class="grid">
      {#each upgrades as upgrade}
        <button
          class="upgrade"
          on:click={() => {
            if (clicks >= upgrade.cost) {
              if (upgrade.multiplier) {
                multiplier = multiplier + upgrade.multiplier;
                clicks -= upgrade.cost;
              }
              if (upgrade.worker && clicks) {
                worker_multiplier = worker_multiplier + 1;
                workers = [upgrade.name, ...workers];
                /* start "clicking" every 1000 ms */
                setInterval(increment, 1000);
                clicks -= upgrade.cost;
              }
            } else {
              alert("Click some more first!");
            }
          }}
        >
          <span>{upgrade.name}</span>
          <span>{upgrade.cost * worker_multiplier }</span>
        </button>
      {/each}
    </div>
  </header>
  <div class="game">
    <button on:click={increment} class="clicker">
      <span class="clicks">{clicks}</span>
      <span class="pointtext">PPC: {multiplier}</span>
    </button>
  </div>
  <footer>
    <div class="panelright">
      <div>
        <span>Workers</span>
        <hr />
        <div class="shop">
          {#each workers as worker}
            <div class="worker">{worker}</div>
          {/each}
        </div>
      </div>
      <hr />
    </div>
  </footer>
</article>
<details>
  <summary>Baka dom hemma själv</summary>
  <h6>Ingredienser</h6>
  <p>Arla® Svenskt Smör - 100 g</p>
  <p>Strösocker - 1 dl</p>
  <p>Farinsocker - ½ dl</p>
  <p>Ägg - 1</p>
  <p>Vetemjöl - 2 dl</p>
  <p>Bikarbonat - ½ tsk</p>
  <p>Salt - ½ tsk</p>
  <p>Vaniljsocker - ½ tsk</p>
  <p>Mörk choklad - 100 g</p>
  
  <h6>Gör Såhär</h6>
  <p>Smält smöret långsamt i en kastrull, ta det från plattan så fort det har smält och låt det svalna. Om smöret är för varmt så smälter chokladbitarna ut i smeten.</p>
  <p>Hacka chokladen grovt. Rör ner socker, farinsocker och ägg i kastrullen. Blanda bikarbonat, salt och vaniljsocker i mjölet och rör ner det tillsammans med chokladen.</p>
  <p>Kyl smeten väl, minst 2h.</p>
  <p>Rulla den kylda degent till bollar och placera på en plåt med bakplåtspapper. Lägg dem inte för tätt eftersom de flyter ut något i ugnen. Det är lagom med nio kakor på varje plåt.</p>
  <p>Sätt ugnen på 200°.</p>  
  <p>Baka kakorna i mitten av ugnen i ca 10 min. Låt kakorna kallna på plåten.</p>
 
  <h6>Klar!!</h6>
  </details>
<style>
  .shop {
    display: grid;
    grid-auto-flow: row; /* default */
    gap: 8px;
    grid-template-rows: repeat(3, 1fr);
    grid-template-columns: repeat(3, 1fr);
  }

  .upgrade {
    width: 100%;
    height: 100%;
    border: 4px solid rgb(91, 47, 0);
    background-color: rgb(116, 65, 31);
    background-size: bottom;
    background-image: url("https://i0.wp.com/www.thearcadecorner.com/wp-content/uploads/2019/07/blast-furnace.jpg?fit=780%2C439&ssl=1");
    place-items: center;
    place-content: center;
    display: flex;
    flex-direction: column;
  }

  .worker {
    width: 100%;
    height: 100%;
    border: 1px solid rgb(91, 47, 0);
    background-image: url("https://cdn.dribbble.com/users/210795/screenshots/16073734/media/cab58d1106fe8b9e903ea49676e3133f.png?compress=1&resize=400x300");
    place-items: center;
    place-content: center;
    display: flex;
  }

  .game {
    height: 50vh;
    display: flex;
    flex-direction: column;
    place-items: center;
    place-content: center;
  }
  .clicker {
    clip-path: rectangel();
    display: flex;
    border: 4px solid rgb(91, 47, 0);
    height: 100%;
    width: 100%;
    flex-direction: column;
    place-items: center;
    place-content: center;
    background-image: url("https://images.arla.com/recordid/8604230E-81A2-4982-A595B34571D919EB/salted-chocolate-chip-cookies.jpg?width=1200&height=630&mode=crop&crop=(0,520,0,-432)");
    background-size: cover;
    background-position: 0px -100px;
  }

  .panelright {
    height: 100%;
    display: flex;
    flex-direction: column;
    gap: 16px;
  }

  .clicks {
    font-size: 100px;
    font-weight: bold;
  }

  .pointtext {
    color: rgb(255, 255, 255);
    font-size: 35px;
    font-weight: bold;
  }
</style>
