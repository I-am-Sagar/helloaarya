<script lang="ts">
    import { page } from '$app/stores';
    import { fade } from 'svelte/transition';
    
    let isMobileMenuOpen = false;

    // Function to close mobile menu
    function closeMenu() {
        isMobileMenuOpen = false;
    }
</script>

<nav class="fixed w-full top-0 z-50 bg-white/80 backdrop-blur-sm border-b border-rose-100 font-medium">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex justify-between items-center h-16">
            <!-- Logo -->
            <a href="/" class="text-4xl font-cursive text-rose-700 hover:text-rose-900 transition-colors">
                Hello Aarya!
            </a>

            <!-- Desktop Menu -->
            <div class="hidden md:flex space-x-8">
                <a 
                    href="/" 
                    class="text-gray-600 hover:text-rose-700 transition-colors { $page.url.pathname === '/' ? 'text-rose-700 border-b-2 border-rose-400' : '' }"
                >
                    Home
                </a>
                <a 
                    href="/sorry" 
                    class="text-gray-600 hover:text-rose-700 transition-colors { $page.url.pathname === '/sorry' ? 'text-rose-700 border-b-2 border-rose-400' : '' }"
                >
                    A Small Apology
                </a>
            </div>

            <!-- Mobile Menu Button -->
            <button
                on:click={() => isMobileMenuOpen = !isMobileMenuOpen}
                class="md:hidden p-2 rounded-lg text-gray-600 hover:text-rose-700 hover:bg-rose-50 transition-colors"
            >
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
                </svg>
            </button>
        </div>
    </div>

    <!-- Mobile Menu -->
    {#if isMobileMenuOpen}
        <div transition:fade class="absolute w-full bg-white/95 backdrop-blur-sm md:hidden">
            <div class="px-4 pt-2 pb-4 space-y-2">
                <a 
                    href="/" 
                    on:click={closeMenu}
                    class="block py-2 text-gray-600 hover:text-rose-700 hover:bg-rose-50 rounded-lg px-4 transition-colors"
                >
                    Home
                </a>
                <a 
                    href="/sorry" 
                    on:click={closeMenu}
                    class="block py-2 text-gray-600 hover:text-rose-700 hover:bg-rose-50 rounded-lg px-4 transition-colors"
                >
                    A Small Apology
                </a>
            </div>
        </div>
    {/if}
</nav>
