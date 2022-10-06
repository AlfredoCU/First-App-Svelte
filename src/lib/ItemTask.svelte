<script>
  export let tasks;
</script>

<!-- Iterar elementos -->
<!-- Acceder al elemento, indice e id para generar un elemento unico -->
<ul>
  {#each tasks as task, num (task.id)}
    <li>
      {num + 1}: {task.name}
      <!-- Condicional -->
      {#if task.done}
        <em>- Terminado</em>
      {/if}
    </li>
    <!-- Si no hay elementos mostrar -->
  {:else}
    <p class="no-task">No hay tareas :D</p>
  {/each}
</ul>

<style>
  ul {
    text-align: left;
  }

  .no-task {
    text-align: center;
  }
</style>
