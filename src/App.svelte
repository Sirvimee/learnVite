<script>
  import ItemList from "./lib/ItemList.svelte";
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

<div class="container mx-auto mt-10 text-center">
  <input type="text" class="input input-bordered input-accent w-full max-w-xs" bind:value={message} on:keydown={keydown} />
  <button on:click={add} class="btn btn-md btn-primary">Add</button>
  <br><br>
  <ItemList title="All items" bind:items={items}></ItemList>
  <br>
  <ItemList title="Done items" bind:items={doneItems}></ItemList>
  <br>
  <ItemList title="Not Done items" bind:items={notDoneItems}></ItemList>
</div>

