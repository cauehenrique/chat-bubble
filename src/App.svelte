<script lang="ts">
  import Message from "./lib/message.svelte"
  import popSound from "./assets/pop.wav"

  const messageAudio = new Audio(popSound)

  let newMessage = ""
  let messages = [
    "Welcome! Record this page and remove it's green screen inside your video editor. 🙌✨",
  ]

  function handleSubmit() {
    if (!newMessage) return

    messages = [...messages, newMessage]
    newMessage = ""

    messageAudio.play()
  }
</script>

<div id="container">
  <div id="messages">
    {#each messages as message}
      <Message text={message} />
    {/each}
  </div>

  <form on:submit|preventDefault={handleSubmit} autocomplete="off">
    <input
      id="new-message-input"
      type="text"
      spellcheck="false"
      bind:value={newMessage}
    />
  </form>
</div>

<style>
  #container {
    display: flex;
    flex-direction: column;

    height: 100vh;
    min-height: 100vh;
  }

  #messages {
    padding: 1rem;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: end;
    gap: 0.5rem;
    overflow: hidden;
  }

  form {
    padding: 1rem;
  }

  #new-message-input {
    outline: 0;
    border: 0;

    width: 100%;
    font-size: 2rem;
    background-color: #fff;
    padding: 0.75rem 0.95rem;
    border-radius: 0.75rem;
  }
</style>
