<script>
    import { onMount } from 'svelte';

    import edinburghImage from '$lib/images/edinburgh1.jpg';
    import aaryaImage from '$lib/images/aarya.jpeg';
    
    let isFlippedEdinburgh = false;
    let isFlippedHer = false;
    let message = "";
    
    /**
   * @param {string} choice
   */
    function handleImageClick(choice) {
      if (choice === 'her') {
        isFlippedHer = true;
        message = "You have a good choice!";
      } else {
        isFlippedEdinburgh = true;
        message = "Did you not see the other pic?";
      }
      
      // Reset the card after 3 seconds
      setTimeout(() => {
        if (choice === 'her') {
          isFlippedHer = false;
        } else {
          isFlippedEdinburgh = false;
        }
      }, 3000);
    }
    
    onMount(() => {
      // Add any initialization logic here if needed
    });
</script>
  
<section class="pt-24 min-h-[70vh] flex justify-center px-4 sm:px-6 lg:px-8 bg-white">
    <div class="w-full max-w-4xl">
        <h2 class="text-4xl sm:text-5xl font-cursive text-rose-700 text-center mb-8">Thank You For Being With Me!</h2>
        <p class="text-xl sm:text-2xl font-cursive text-gray-700 text-center mb-8">Why? Because you made my time in Edinburgh more memorable!</p>
        
        <div class="interactive-instruction mb-8">
            <p class="text-lg text-gray-600 text-center font-light">Pick the more beautiful image</p>
        </div>

        <div class="flex flex-col sm:flex-row justify-center items-center gap-4">
            <!-- Edinburgh Card -->
            <div class="flip-card-container" class:flipped={isFlippedEdinburgh}>
                <div class="flip-card" on:click={() => handleImageClick('edinburgh')}>
                    <div class="flip-card-front">
                        <img src={edinburghImage} alt="Edinburgh" class="card-image">
                        <div class="card-label">Edinburgh</div>
                    </div>
                    <div class="flip-card-back">
                        <h3 class="text-2xl font-cursive text-rose-700 mb-4">{message}</h3>
                        <div class="text-5xl mb-4">
                            {message.includes("good choice") ? '😍' : '🤔'}
                        </div>
                    </div>
                </div>
            </div>

            <!-- Her Card -->
            <div class="flip-card-container" class:flipped={isFlippedHer}>
                <div class="flip-card" on:click={() => handleImageClick('her')}>
                    <div class="flip-card-front">
                        <img src={aaryaImage} alt="Her" class="card-image">
                        <div class="card-label">You</div>
                    </div>
                    <div class="flip-card-back">
                        <h3 class="text-2xl font-cursive text-rose-700 mb-4">{message}</h3>
                        <div class="text-5xl mb-4">
                            {message.includes("good choice") ? '😍' : '🤔'}
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <p class="text-md sm:text-lg text-gray-600 text-center mt-8 font-light mb-8">Yeah, I know online cheesy hona tough hai, but trust me you'll get more cheesy lines when I'll be around! 🙈</p>
    </div>
</section>
  
<style>
    /* Custom fonts */
    :global(.font-cursive) {
        font-family: 'Dancing Script', cursive;
    }
    
    :global(.font-romantic) {
        font-family: 'Lora', serif;
        font-style: italic;
    }
    
    /* Card flip effect - improved */
    .flip-card-container {
        perspective: 1000px;
        width: 300px;
        height: 400px;
        margin: 0 auto;
    }
    
    .flip-card {
        position: relative;
        width: 100%;
        height: 100%;
        transition: transform 0.8s;
        transform-style: preserve-3d;
        cursor: pointer;
    }
    
    .flip-card-container.flipped .flip-card {
        transform: rotateY(180deg);
    }
    
    .flip-card-front, .flip-card-back {
        position: absolute;
        width: 100%;
        height: 100%;
        -webkit-backface-visibility: hidden;
        backface-visibility: hidden;
        border-radius: 12px;
        box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }
    
    .flip-card-front {
        background-color: #f8f8f8;
        overflow: hidden;
    }
    
    .card-image {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }
    
    .card-label {
        position: absolute;
        bottom: 0;
        left: 0;
        right: 0;
        background-color: rgba(210, 55, 96, 0.8);
        color: white;
        padding: 8px 0;
        text-align: center;
        font-weight: bold;
    }
    
    .flip-card-back {
        background: linear-gradient(145deg, #fcf1f3, #fff);
        transform: rotateY(180deg);
        padding: 20px;
        text-align: center;
    }
    
    .interactive-instruction {
        background-color: rgba(210, 55, 96, 0.1);
        border-radius: 0.5rem;
        padding: 0.75rem;
        margin-bottom: 1.5rem;
        border-left: 4px solid #d23760;
        max-width: 80%;
        margin-left: auto;
        margin-right: auto;
    }
</style>