<script>
  import Slider from "$lib/slider.svelte";
  let rvMPG = 10;
  let rvAverageCostPerNight = 45;
  let rvDepreciation = 10000;

  let carMPG = 30;
  let carAverageCostPerNight = 90;
  let carDepreciation = 5000;

  let mileGoals = 3000;
  let dayGoals = 90;
  let gasCostPerGallon = 5;

  $: rvCost =
    Math.ceil(
      ((mileGoals / rvMPG) * gasCostPerGallon +
        rvAverageCostPerNight * dayGoals +
        rvDepreciation) *
        100
    ) / 100;

  $: carCost =
    Math.ceil(
      ((mileGoals / carMPG) * gasCostPerGallon +
        carAverageCostPerNight * dayGoals +
        carDepreciation) *
        100
    ) / 100;
</script>

<div class="hero">
  <div class="hero-content">
    <h1>Should you grab an RV or get a car and stay in AirBNBs?</h1>
  </div>
</div>
<h2>Rv Specs</h2>
<div class="sliderContainer">
  <Slider
    bind:value="{rvMPG}"
    min="1"
    max="25"
    label="The RVs miles per gallon"
  />
  <Slider
    bind:value="{rvAverageCostPerNight}"
    min="0"
    max="75"
    label="The RVs average cost per night"
  />
  <Slider
    bind:value="{rvDepreciation}"
    min="2000"
    max="25000"
    label="Cost to purchase the RV minus how much it gets sold for"
  />
</div>

<h2>Car Specs</h2>
<div class="sliderContainer">
  <Slider
    bind:value="{carMPG}"
    min="10"
    max="60"
    label="The Cars miles per gallon"
  />
  <Slider
    bind:value="{carAverageCostPerNight}"
    min="30"
    max="200"
    label="The Cars average cost per night"
  />
  <Slider
    bind:value="{carDepreciation}"
    min="1000"
    max="10000"
    label="Cost to purchase the Car minus the cost to sell it"
  />
</div>

<h2>Trip duration</h2>
<div class="sliderContainer">
  <Slider
    bind:value="{mileGoals}"
    min="0"
    max="5000"
    label="Total miles we want to travel"
  />
  <Slider
    bind:value="{dayGoals}"
    min="0"
    max="100"
    label="How long the trip will be in days"
  />
  <Slider
    bind:value="{gasCostPerGallon}"
    min="0"
    max="7"
    label="How much does gas cost"
  />
</div>

<h3>
  Total RV cost: {rvCost}
</h3>
<h3>
  Total Car cost: {carCost}
</h3>

{#if rvCost > carCost}
  <h2>The car is cheaper</h2>
{:else}
  <h2>The rv is cheaper is cheaper</h2>
{/if}

<style>
  .hero {
    background: url("/hero.jpg") no-repeat center center fixed;
    min-height: 200px;
    -webkit-background-size: cover;
    -moz-background-size: cover;
    -o-background-size: cover;
    background-size: cover;
    padding-top: 50px;
  }
  .hero-content {
    text-align: center;
    background: rgba(255, 255, 255, 0.5);
    padding: 25px;
    margin: 25px;
  }
  .sliderContainer {
    display: flex;
    justify-content: space-between;
    border-bottom: 1px solid #888;
    padding: 0 20px 20px 20px;
  }
  h2 {
    padding: 20px;
  }
</style>
