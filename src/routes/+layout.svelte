<script>
import "../app.css";

import Navbar from "$lib/components/Navbar.svelte";
import Footer from "$lib/components/Footer.svelte";
</script>

<Navbar />

<main class="min-h-screen pt-16"> <!-- Add padding-top to account for the fixed navbar -->
    <slot />
</main>

<Footer />
