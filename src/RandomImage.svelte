<script>
  import { createEventDispatcher } from "svelte";
  import images from "./images.js";

  const dispatch = createEventDispatcher();
  let notification = "";
  let image = {};

  const getRandomImage = () => {
    image = images[Math.floor(Math.random() * images.length)];
  };

  getRandomImage();

  const choose = choice => {
    if (image.isAnimal) {
      if (choice === "animal") {
        notification = "YES! Correct. That is definitely an animal.";
        dispatch("addAnimal", image.url);
      } else {
        notification = "Incorrect. But do not be sad, it is a difficult game.";
      }
    } else {
      if (choice === "boris") {
        notification =
          "Absolutely right. You are truly proficient in The Boris.";
      } else {
        notification = "Wrong! That is Boris you fool!";
      }
    }
    getRandomImage();
  };
</script>

<style>
  img {
    max-width: 300px;
  }

  .notification {
    padding: 16px;
    background-color: rgb(160, 160, 255);
  }
</style>

{#if notification.length > 0}
  <div class="notification">{notification}</div>
{/if}

<h2>Is this an ANIMAL or is it BORIS JOHNSON?</h2>

<img src={image.url} alt="animal or bojo who knows" />

<button on:click={() => choose('animal')}>EE-I-EE-I-OH</button>
<button on:click={() => choose('boris')}>Brexit Means Brexit</button>
