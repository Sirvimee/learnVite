<script>
    export let items;
    export let title;
</script>

<h1 class="text-xl">{title}</h1>
<ul>
  {#each items as item}
    <li>
      {item.text}
      <input type="checkbox" bind:checked={item.isDone} />
    </li>
  {/each}
</ul>