<script>
  let message = "Hello Svelte";
  let items = [
    { text: "Piim", isDone: false },
    { text: "Leib", isDone: false },
    { text: "Sai", isDone: false },
  ];

  $: doneItems = items.filter(item => item.isDone);
  $: notDoneItems = items.filter(item => !item.isDone);

  function add() {
    //if message not emty, then added
    if (message.trim() !== "") {
      items = [...items, { text: message, isDone: false }];
    }
    message = "";
  }

  //can use "Enter" key
  function keydown(evt) {
    if (evt.key === "Enter") {
      add();
    }
  }
</script>

<input type="text" bind:value={message} on:keydown={keydown} />
<button on:click={add}>Add</button>

<h1>All items</h1>
<ul>
  {#each items as item}
    <li>
      {item.text}
      <input type="checkbox" bind:checked={item.isDone} />
    </li>
  {/each}
</ul>

<h1>Done items</h1>
<ul>
  {#each doneItems as item}
    <li>
      {item.text}
      <input type="checkbox" bind:checked={item.isDone} />
    </li>
  {/each}
</ul>

<h1>Not done items</h1>
<ul>
  {#each notDoneItems as item}
    <li>
      {item.text}
      <input type="checkbox" bind:checked={item.isDone} />
    </li>
  {/each}
</ul>
