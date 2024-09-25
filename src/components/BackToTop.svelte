<script>
    import { onMount } from 'svelte';
    import { fly } from 'svelte/transition';
  
    let showButton = false;
  
    onMount(() => {
      const handleScroll = () => {
        const landingDiv = document.getElementById('landing');
        if (landingDiv) {
          const landingBottom = landingDiv.getBoundingClientRect().bottom;
          showButton = window.scrollY > landingBottom;
        }
      };
  
      window.addEventListener('scroll', handleScroll);
  
      return () => {
        window.removeEventListener('scroll', handleScroll);
      };
    });
  
    const scrollToTop = () => {
      window.scrollTo({ top: 0, behavior: 'smooth' });
    };
  </script>
  
  <style>
    .back-to-top {
      @apply fixed bottom-8 right-8 btn glass cursor-pointer;
    }
  </style>
  
  {#if showButton}
    <div class="back-to-top" on:click={scrollToTop} transition:fly={{ x: 200, duration: 300 }}>
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16" fill="currentColor" class="size-4">
            <path fill-rule="evenodd" d="M8 14a.75.75 0 0 1-.75-.75V4.56L4.03 7.78a.75.75 0 0 1-1.06-1.06l4.5-4.5a.75.75 0 0 1 1.06 0l4.5 4.5a.75.75 0 0 1-1.06 1.06L8.75 4.56v8.69A.75.75 0 0 1 8 14Z" clip-rule="evenodd" />
        </svg>          
    </div>
  {/if}