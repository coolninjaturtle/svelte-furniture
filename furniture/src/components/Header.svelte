<script>
    import { page } from '$app/stores';
    import { derived } from "svelte/store";

    const activeRoute = derived(page, $page => $page.url.pathname);
</script>


<header class="bg-[#f8f4e3] px-8 py-4 flex items-center justify-between shadow-md z-10 sticky top-0 w-full">
    <div class="flex items-center justify-between p-4 py-2">
        <a href="/">
            <h1 class="poppins-bold text-2xl">
                Sajilo <span class="text-indigo-400">Deals</span>
            </h1>
        </a>
    </div>
    <nav class="flex space-x-12">
      <a href="/store" class={$activeRoute === "/store" ? "activeNavBarItem" : "inactiveNavBarItem"}>Store</a>
      <a href="/contact" class={$activeRoute === "/contact" ? "activeNavBarItem" : "inactiveNavBarItem"}>Contact Us</a>
    </nav>
    <div class="flex space-x-4">
        <a href="/login" class="bg-indigo-500 text-white px-4 py-2 rounded-md hover:bg-indigo-600 poppins-bold">Login</a>
        <a href="/signup" class="bg-white text-indigo-500 border border-indigo-500 px-4 py-2 rounded-md hover:bg-indigo-50 poppins-bold">Sign Up</a>
    </div>
</header>

<style>

.inactiveNavBarItem{
    font-family: "Poppins", sans-serif;
    font-weight: 500;
    font-style: normal;
    position: relative;
    color: #1f2937;
}

.activeNavBarItem {
    font-family: "Poppins", sans-serif;
    font-weight: 700;
    font-style: normal;
    position: relative;
    color: #818cf8; /* text-indigo-400 equivalent in Tailwind */
}
  
.inactiveNavBarItem::before {
    content: '';
    position: absolute;
    width: 0;
    height: 4px; /* Thickness of the underline */
    bottom: -2px;
    left: 0;
    background-color: #1f2937; /* Color of the underline */
    visibility: hidden;
    transition: all 0.3s ease-in-out;
}
  
.inactiveNavBarItem:hover::before {
    visibility: visible;
    width: 100%;
    right: 0;
}

.activeNavBarItem::before {
    content: '';
    position: absolute;
    width: 50%; /* Half underline */
    height: 4px; /* Thickness of the underline */
    bottom: -2px;
    left: 0;
    background-color: #818cf8; /* text-indigo-400 equivalent in Tailwind */
}

.activeNavBarItem::after {
    content: '';
    position: absolute;
    width: 0;
    height: 4px; /* Thickness of the underline */
    bottom: -2px;
    right: 0;
    background-color: #818cf8; /* text-indigo-400 equivalent in Tailwind */
    visibility: hidden;
    transition: all 0.3s ease-in-out;
}

.activeNavBarItem:hover::after {
    visibility: visible;
    width: 50%;
}

</style>
