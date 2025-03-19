<script>
    import aarya2 from "$lib/images/aarya2.jpeg";
    import sagar_coffee from "$lib/images/sagar_table.jpeg";
    import sagar_srk from "$lib/images/Sagar_srk.jpeg";
</script>

<section class="bg-gradient-to-br from-rose-50 to-rose-100 py-16">
  <div class="container mx-auto text-center">
    <h2 class="text-5xl font-extrabold font-cursive text-rose-700 mb-12">We Will Do Great Things Once We Meet</h2>
    
    <!-- First Content Block: Coffee, Chai & Chill -->
    <div class="flex flex-col md:flex-row items-center mb-12 space-y-6 md:space-y-0">
      <div class="md:w-1/2 p-6 flex justify-center">
        <div class="max-w-md">
          <h3 class="text-3xl font-semibold font-cursive text-rose-700 mb-4">Coffee, Chai & Chill</h3>
          <p class="text-lg font-light text-black">We'll hit a cafe, enjoy a cup of coffee, and have some easy-going chats—just a moment to relax and unwind with me.</p>
        </div>
      </div>
      <div class="md:w-1/2 flex justify-center">
        <div class="w-3/4 md:w-[52%] p-6 bg-white rounded-xl shadow-lg">
          <img src={sagar_coffee} alt="Photo with coffee" class="w-full h-full object-cover rounded-lg">
        </div>
      </div>
    </div>
  
    <!-- Second Content Block: Explorer Mode -->
    <div class="flex flex-col md:flex-row-reverse items-center mb-12 space-y-6 md:space-y-0">
      <div class="md:w-1/2 p-6 flex justify-center">
        <div class="max-w-md">
          <h3 class="text-3xl font-semibold font-cursive text-rose-700 mb-4">Explorer Mode</h3>
          <p class="text-lg font-light text-black">How about we create some great memories in Mumbai—cozy walks on beaches, delicious food (I’m a pretty good cook, by the way), and discovering some hidden gems together?</p>
        </div>
      </div>
      <div class="md:w-1/2 flex justify-center">
        <div class="w-3/4 md:w-[70%] p-6 bg-white rounded-xl shadow-lg">
          <img src={aarya2} alt="Her photo in Edinburgh streets" class="w-full h-full object-cover rounded-lg">
        </div>
      </div>
    </div>
  
    <!-- Third Content Block: Filmy Partner -->
    <div class="flex flex-col md:flex-row items-center mb-12 space-y-6 md:space-y-0">
      <div class="md:w-1/2 p-6 flex justify-center">
        <div class="max-w-md">
          <h3 class="text-3xl font-semibold font-cursive text-rose-700 mb-4">Filmy Partner</h3>
          <p class="text-lg font-light text-black">Let's binge-watch rom-coms and have a good laugh. And if our choices don't meet well, we'll just laugh it off with "Ese bade bade shehro mein esi chhoti chhoti baatein hoti rehti hai Senorita!"</p>
        </div>
      </div>
      <div class="md:w-1/2 flex justify-center">
        <div class="w-3/4 md:w-[90%] p-6 bg-white rounded-xl shadow-lg">
          <img src={sagar_srk} alt="Me posing SRK pic" class="w-full h-full object-cover rounded-lg">
        </div>
      </div>
    </div>
  </div>
</section>