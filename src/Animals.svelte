<script>
  export let animals;
</script>

<style>
  img {
    max-width: 250px;
  }
</style>

{#if animals.length === 0}
  <p>You have won no animals. For shame.</p>
{:else}
  <div class="won-animals">
    <h3>Your Won Animals!</h3>
    {#each animals as animal}
      <img src={animal} alt="An animal" />
    {/each}
  </div>
{/if}
