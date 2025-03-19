<script>
  import Hero from "$lib/components/Hero.svelte";
  import Joke from "$lib/components/Joke.svelte";
  import ThankYou from "$lib/components/ThankYou.svelte";
</script>


<main>
    <Hero />
    <ThankYou />
    <Joke />
</main>

<style>
    main {
      width: 100%;
      /* Add any global styles for the page container here */
    }
  </style>