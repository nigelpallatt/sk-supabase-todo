<script>
import supabase from "$lib/db";
import { onMount } from "svelte";


let todos = [];

onMount(async()=>{

let { data, error } = await supabase
  .from('todos')
  .select('*');
  todos = data;

})
</script>

{#each todos as todo}
<div class="todos">
    <input type="checkbox" checked={todo.siComplete}>
    <input type="text" value={todo.task}>
    <button>Delete</button>
</div>
{:else}
<p>No todos found</p>
{/each}

<style>
    .todos{
        display: flex;
        margin-bottom: .25em;
    }
</style>