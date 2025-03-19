<script>
  import { onMount } from 'svelte';
  
  let visible = false;
  
  onMount(() => {
    // Trigger animation after component mounts
    setTimeout(() => {
      visible = true;
    }, 300);
  });
</script>

<section class="pt-24 min-h-[60vh] flex items-center justify-center px-4 sm:px-6 lg:px-8 bg-gradient-to-br from-rose-50 to-rose-100">
  <div class="max-w-4xl w-full flex justify-center translate-y-[-15%] sm:translate-x-0 lg:translate-x-[-20%]"> <!-- Center on small/medium screens, left-align on larger screens -->
    <div 
      class="relative overflow-hidden rounded-2xl bg-white/90 backdrop-blur-sm shadow-xl p-6 sm:p-8 md:p-12 transform transition-all duration-1000 ease-out {visible ? 'translate-y-0 opacity-100' : 'opacity-0'} w-full sm:w-auto">
      <div class="relative z-10">
        <h1 class="text-3xl sm:text-4xl md:text-5xl font-cursive text-rose-700 mb-4">Hello Aarya,</h1>
        <p class="text-3xl sm:text-2xl md:text-2xl text-gray-700 mb-2 font-cursive">Welcome to your little digital space.</p>
        <p class="text-base sm:text-lg text-gray-600 mt-6 max-w-2xl mx-auto font-light">
          Relax. It's just a small gesture to make feel a little more special!
        </p>
      </div>
      
      <!-- Decorative elements -->
      <div class="absolute top-0 right-0 w-24 h-24 sm:w-32 sm:h-32 bg-gradient-to-br from-rose-200 to-rose-300 rounded-full -mr-8 sm:-mr-12 -mt-8 sm:-mt-12 opacity-40 animate-float"></div>
      <div class="absolute bottom-0 left-0 w-32 h-32 sm:w-40 sm:h-40 bg-gradient-to-tr from-rose-200 to-rose-100 rounded-full -ml-12 sm:-ml-16 -mb-12 sm:-mb-16 opacity-30 animate-float-delay"></div>
      <div class="absolute top-1/2 left-1/4 w-12 h-12 sm:w-16 sm:h-16 bg-rose-100 rounded-full opacity-50 animate-pulse"></div>
      
      <!-- Squiggly line -->
      <svg class="absolute bottom-8 right-8 w-24 h-6 sm:w-32 sm:h-8 text-rose-300 opacity-40 animate-slide" viewBox="0 0 100 20" xmlns="http://www.w3.org/2000/svg">
        <path d="M0,10 Q10,5 20,10 T40,10 T60,10 T80,10 T100,10" fill="none" stroke="currentColor" stroke-width="2" />
      </svg>
      
      <!-- Dots pattern -->
      <div class="absolute top-8 sm:top-12 right-8 sm:right-10 w-16 h-16 sm:w-20 sm:h-20 opacity-20 animate-spin-slow">
        <div class="grid grid-cols-3 gap-1 sm:gap-2">
          {#each Array(9) as _, i}
            <div class="w-1.5 h-1.5 sm:w-2 sm:h-2 rounded-full bg-rose-500"></div>
          {/each}
        </div>
      </div>
    </div>
  </div>
</section>

<style>
  /* Add custom animations */
  @keyframes float {
    0% { transform: translateY(0) rotate(0deg); }
    50% { transform: translateY(-10px) rotate(5deg); }
    100% { transform: translateY(0) rotate(0deg); }
  }
  
  @keyframes float-delay {
    0% { transform: translateY(0) rotate(0deg); }
    50% { transform: translateY(-15px) rotate(-5deg); }
    100% { transform: translateY(0) rotate(0deg); }
  }
  
  @keyframes slide {
    0% { transform: translateX(0); }
    50% { transform: translateX(20px); }
    100% { transform: translateX(0); }
  }
  
  @keyframes spin-slow {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
  }
  
  /* Apply animations to elements */
  .animate-float {
    animation: float 8s ease-in-out infinite;
  }
  
  .animate-float-delay {
    animation: float-delay 9s ease-in-out infinite;
  }
  
  .animate-slide {
    animation: slide 12s linear infinite;
  }
  
  .animate-spin-slow {
    animation: spin-slow 30s linear infinite;
  }
</style>
