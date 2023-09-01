<script>
  import Chat from './Chat.svelte';
  import ChatButton from './ChatButton.svelte';

  let isChatOpen = false;

  // Function to open the chat
  function openChat() {
    isChatOpen =  !isChatOpen;
  }
</script>

<main>
  <div>
    {#if isChatOpen}
      <Chat />
    {/if}
    <ChatButton on:open-chat={openChat} />
  </div>
</main>
