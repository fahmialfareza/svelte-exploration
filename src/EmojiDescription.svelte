<script>
  import { onMount, onDestroy, beforeUpdate, afterUpdate } from 'svelte';

  let description = '';
  $: character = description.length;
  $: words = description.split(' ').length;

  $: if (character > 10) {
      console.log(`Description ${description}`);
      console.log('----')
    }

  function handleSubmit(event) {
    console.log('Form Submitted. Thanks!');
    description = '';
  }

  onMount(() => {
    console.log('onMount');
  });

  onDestroy(() => {
    console.log('onDestroy');
  });

  beforeUpdate(() => {
    console.log('beforeUpdate');
  });

  afterUpdate(() => {
    console.log('afterUpdate');
  })
</script>

<style>
  div {
    margin-top: 1em;
    margin-bottom: 1em;
  }
</style>

<div class="form-group">
  <p>{description}</p>
  <form on:submit|preventDefault={handleSubmit}>
    <textarea bind:value={description} rows="7"></textarea>
    <button type="submit">Save</button>
  </form>
  
  <p>Character count: {character}</p>
  <p>Words count: {words}</p>
</div>