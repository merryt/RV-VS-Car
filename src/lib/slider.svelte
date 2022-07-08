<script>
  export let value = "";
  export let label = "";
  export let min = 0;
  export let max = 100;
</script>

<div class="slider">
  <label for="carMPG">{label}</label>
  <input
    type="range"
    min="{min}"
    max="{max}"
    class="slider"
    id="carMPG"
    bind:value
  />
  {value}
</div>
