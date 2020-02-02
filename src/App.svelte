<script>
  import RandomImage from "./RandomImage.svelte";
  import Animals from "./Animals.svelte";

  let animals = [];

  const addAnimal = event => {
    const animalImgUrl = event.detail;
    animals = [...animals, animalImgUrl];
  };
</script>

<h1>Old MacDonald's Playground</h1>

<RandomImage on:addAnimal={addAnimal} />
<Animals {animals} />
