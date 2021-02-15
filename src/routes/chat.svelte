<script>
  export let title = 'Message App';
  let msg = '';
  let selectedUser = '';
  let messages = [
    {
      id: 1,
      text: 'My first Message',
      user: 'Rehan',
      createdAt: new Date(),
      className: 'left',
    },
  ];
  function createMessage(message) {
    messages = messages.concat(message);
  }
</script>

<div
  style="width: 700px;min-height: 500px; border: 1px solid black;padding: 5px"
>
  <h3>{title}</h3>
  {#each messages as { text, user, createdAt, className }}
    <div class={className}>
      <p>{text}</p>
      <small>{createdAt.toLocaleString()}</small>
      <p>{user}</p>
    </div>
  {/each}
  <div style="clear: both;" />
  <input bind:value={msg} />
  <button
    on:click={e => {
      e.preventDefault();
      createMessage({
        id: messages[0].id + 1,
        text: msg,
        user: selectedUser,
        createdAt: new Date(),
        className: selectedUser === 'Haseeb' ? 'right' : 'left',
      });
    }}>Send</button
  >
  <select bind:value={selectedUser}>
    <option value="Rehan">Sender</option>
    <option value="Haseeb">Receiver</option>
  </select>
</div>

<style>
  .left {
    float: left;
  }
  .right {
    float: right;
  }
</style>
