<!-- Evento onclick -->
<script>
  // Crear un estado
  let count = 0;

  // Actualizar ese estado
  const Increment = () => (count += 1);
</script>

<!-- Mostrar nuestro estado y usando la función que actualiza mi estado -->
<div class="counter">
  <button on:click={Increment}>
    Counter: {count}
  </button>
</div>

<style>
  .counter {
    margin: 1rem 0;
  }
</style>
