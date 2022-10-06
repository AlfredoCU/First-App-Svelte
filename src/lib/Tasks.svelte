<script>
  import ItemTask from "./ItemTask.svelte";

  let tasks = [
    { id: "845324324423", name: "Comprar computadora", done: true },
    { id: "213423423324", name: "Limpiar casa", done: false },
    { id: "954643677641", name: "Enviar correos", done: true },
    { id: "542931313041", name: "Hacer tareas", done: false },
  ];
</script>

<h2>Tareas:</h2>
<ItemTask {tasks} />

<style>
  h2 {
    text-align: left;
  }
</style>
