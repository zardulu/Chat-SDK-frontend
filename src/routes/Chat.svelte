<script>
    let messages = [];
    let newMessage = '';
    let chatHistory;
    let nextKey = 0; // Initialize key
   
    function sendMessage() {
      if (newMessage.trim() === '') return;
  
      // Append new user message to the existing messages with key
      messages = [
        ...messages,
        { key: nextKey++, text: newMessage, sender: 'user', profilePic: 'user1.png' },
      ];
      newMessage = '';
  
      // Simulate a response from bot
      setTimeout(() => {
        const botResponse = { key: nextKey++, text: 'Hello, how can I help you?', sender: 'bot', profilePic: 'bot1.png' };
  
        
        messages = [...messages, botResponse];
  
        // Scroll to the bottom after a new message is added.
        scrollChatToBottom();
      }, 1500);
    }
  
    function handleKeyDown(event) {
      if (event.key === 'Enter') {
        sendMessage();
      }
    }
  
    function scrollChatToBottom() {
      chatHistory.scrollTop = chatHistory.scrollHeight;
    }
  </script>
  
  
  
  
  <div class="chat-container p-5 border rounded-lg w-96 h-96 flex flex-col justify-end bg-amber-50">
    
    <div class="chat-history flex-grow overflow-y-auto mb-2" bind:this={chatHistory}>

      {#each messages as message (message.key)}

        <div class={`message flex m-2 ${message.sender === 'user' ? 'justify-end' : 'justify-start'}`} key={message.key}>

          {#if message.sender === 'user'}

            <div class="user-bubble bg-blue-500 text-white rounded-tl-xl rounded-tr-xl rounded-bl-xl p-2 max-w-xl">
              <div class="message-text">{message.text}</div>
            </div>

            <img src={message.profilePic} class="profile-pic user-pic w-10 h-10 rounded-[50%] ml-2 shadow-md" alt="User Profile" />

          {:else}

            <img src={message.profilePic} class="profile-pic bot-pic w-10 h-10 rounded-[50%] rounded-full mr-2 shadow-md" alt="Bot Profile" />

            <div class="bot-bubble bg-gray-200 text-gray-800 rounded-tl-xl rounded-tr-xl rounded-br-xl p-2 max-w-xl">
              <div class="message-text">{message.text}</div>
            </div>

          {/if}

        </div>

      {/each}

    </div>
  
    <div class="chat-input flex">
      <input type="text" placeholder="Type a message..." bind:value={newMessage} on:keydown={handleKeyDown} class="flex-grow p-1 border rounded" />
      <button on:click={sendMessage} class="ml-2 p-2 bg-blue-500 text-white rounded">Send</button>
    </div>

  </div>
  
  
