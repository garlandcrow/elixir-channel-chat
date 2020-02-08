<script>
  import { Button, Checkbox, Switch, Snackbar } from 'smelte'

  let newMessageText = ''
  let messages = ['one', 'two', 'three', 'four']

  const submitMessage = () => {
    messages = [...messages, newMessageText]
    newMessageText = ''
  }
</script>

<div class="container flex bg-gray-100">
  <div
    class="m-10 p-4 pr-1 flex-1 rounded bg-blue-50 border border-blue-800 elevation-3 flex flex-col"
  >
    <div class="flex-1 mb-4 pr-3 overflow-scroll flex flex-col">
      {#each messages as msg, idx}
        <div class="message" class:theirs={idx % 2 == 0}>{msg}</div>
      {/each}
    </div>
    <div class="flex">
      <input
        class="p-2 flex-1 rounded border border-blue-800"
        type="text"
        placeholder="type message"
        bind:value={newMessageText}
        on:keydown={({ keyCode }) => keyCode === 13 && submitMessage()}
      />
      <button
        class="p-2 mr-3 ml-2 bg-blue-600 rounded text-white hover:bg-blue-900"
        on:click={submitMessage}
      >
        send
      </button>
    </div>
  </div>
</div>

<style>
  .container {
    height: 100vh;
  }
  .message {
    @apply my-1 p-1 rounded bg-blue-200 text-black;
    align-self: start;
  }
  .message.theirs {
    @apply bg-blue-800 text-white;
    align-self: end;
  }
</style>
