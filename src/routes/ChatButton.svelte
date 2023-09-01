
<script>
    import { createEventDispatcher } from 'svelte';
  
    // Create an event dispatcher
    const dispatch = createEventDispatcher();
  
    // Function to open the chat component
    function openChat() {
      dispatch('open-chat');
    }
  </script>
  
  <button class="fixed bottom-4 right-6 p-3 bg-blue-500 text-white rounded-full shadow-lg" on:click={openChat}>
    <img src='button.png' class="w-10 h-10" alt="chat img" />
    <i class="fas fa-comment"></i>
  </button>
  
