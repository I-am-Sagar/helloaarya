<script>
// @ts-nocheck

    import { onMount } from 'svelte';
  
    let joke = '';
    let setup = '';
    let delivery = '';
    let loading = true;
    let errorMessage = '';
    let jokeCategory = 'Miscellaneous';  // Default category
    let jokeType = '';  // Will be set randomly between 'single' and 'twopart'
  
    const seenJokes = new Set();
  
    // Function to get a joke from the API
    const getJoke = async () => {
      loading = true;
      errorMessage = '';
      let jokeFetched = false;
      let jokeData;
      
      // Randomly select the type of joke: 'single' or 'twopart'
      jokeType = Math.random() < 0.5 ? 'single' : 'twopart';
  
      while (!jokeFetched) {
        const response = await fetch(`https://v2.jokeapi.dev/joke/${jokeCategory}?type=${jokeType}`);
        jokeData = await response.json();
  
        // Check if the joke ID has been seen before
        if (!seenJokes.has(jokeData.id)) {
          seenJokes.add(jokeData.id);
          jokeFetched = true;
        }
      }
  
      // Set the joke to display
      if (jokeData.type === 'single') {
        joke = jokeData.joke;
      } else {
        setup = jokeData.setup;
        delivery = jokeData.delivery;
      }
      loading = false;
    };
  
    // Fetch a joke when the component mounts
    onMount(() => {
      getJoke();
    });
  
    // Function to handle category change
    const changeCategory = (/** @type {{ target: { value: string; }; }} */ event) => {
      jokeCategory = event.target.value;
      getJoke();  // Fetch a new joke based on the new category
    };
  </script>
  
  <style>
    /* Section background color and spacing */
    .joke-container {
      background-color: #f8d7e2; /* Light rose background */
      text-align: center;
      padding: 40px 20px;
      border-radius: 10px;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
      display: flex;
      flex-direction: column;
      align-items: center;
    }
  
    /* Heading style */
    .heading {
      font-size: 2.5em;
      color: #d16d86;
      font-family: 'Playfair Display', serif;
      margin-bottom: 20px;
      text-align: center;
    }
  
    /* Font styles for joke text */
    .joke-text {
      color: #4a4a4a;
      margin: 20px 0;
      padding: 20px;
      background-color: white;
      border-radius: 8px;
      box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
      max-width: 500px;
      margin-left: auto;
      margin-right: auto;
    }
  
    /* Button style with rose color */
    .joke-button {
      background-color: #fa5d7a;  /* Soft rose color */
      padding: 12px 25px;
      border: none;
      color: white;
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
      border-radius: 8px;
      transition: background-color 0.3s ease;
      margin-top: 20px;
    }
  
    .joke-button:hover {
      background-color: #f0757f;  /* Darker rose on hover */
    }
  
    /* Loading text and error message */
    .loading {
      font-style: italic;
      color: grey;
    }
  
    .error {
      color: red;
      font-weight: bold;
    }
  
/* Category dropdown style */
.category-select {
  background-color: #fff4f1; /* Soft background */
  border: 1px solid #f28fa1;  /* Soft rose border */
  font-size: 16px;
  padding: 12px 18px; /* Slightly larger padding for more comfortable interaction */
  border-radius: 5px;
  font-family: 'Quicksand', sans-serif;
  width: 220px; /* Slightly wider for better readability */
  transition: all 0.3s ease;
  margin-bottom: 20px;
  cursor: pointer;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); /* Soft shadow to create depth */
}

/* Dropdown focus effect */
.category-select:focus {
  border-color: #f07f89; /* Darker rose when focused */
  outline: none;
  box-shadow: 0 0 10px rgba(240, 127, 137, 0.6); /* Focus glow effect */
}

/* Hover effect for dropdown */
.category-select:hover {
  border-color: #f07f89; /* Darker rose on hover */
}

/* Option text style */
.category-select option {
  background-color: white;
  padding: 10px;
  font-size: 16px;
  color: #4a4a4a;
  font-family: 'Quicksand', sans-serif;
}

/* Dropdown open state */
.category-select:active {
  background-color: #f8d7e2; /* Slight background change when active */
}
  
    /* Media queries for small screens */
    @media (max-width: 768px) {
      .joke-container {
        flex-direction: column;
      }
  
      .joke-button {
        margin-top: 20px;
      }

      .category-select {
    width: 80%; /* Full width for smaller screens */
    padding: 12px 16px; /* Adjust padding to fit smaller screens */
  }
    }
  </style>
  
  <div class="joke-container">
    <!-- Heading with warm and friendly tone -->
    <div class="text-4xl sm:text-5xl font-cursive text-rose-700 text-center mb-8">But Sagar, Are you even funny?</div>
    
    <!-- Category Selection -->
    <div>
      <label for="category" class="font-romantic">What's your type? (Of course, I meant in jokes!)</label>
      <select id="category" class="category-select m-4" bind:value={jokeCategory} on:change={changeCategory}>
        <option value="Miscellaneous">Light</option>
        <option value="Dark">Dark</option>
        <option value="Programming">Nerd</option>
      </select>
    </div>
  
    <!-- Joke Display -->
    <div class="joke-text">
      {#if loading}
        <p class="loading font-cursive">Loading a new joke for you...</p>
      {:else if errorMessage}
        <p class="error font-cursive">{errorMessage}</p>
      {:else}
        {#if joke}
          <p class="font-light mb-2">{joke}</p>
        {:else}
          <p class="font-light mb-2">{setup}</p>
          <p class="font-light mt-2">{delivery}</p>
        {/if}
      {/if}
    </div>
  
    <!-- Button to get another joke -->
    <button class="joke-button mb-20" on:click={getJoke}>Tell me a joke now!</button>
  </div>
  