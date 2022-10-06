<!-- Se pueden crear dispachadores de eventos personalizados -->
<script>
  // createEventDispatcher es una función factoría
  import { createEventDispatcher } from "svelte";

  // Dispatch es un generador de eventos
  const dispatch = createEventDispatcher();

  const action = () => {
    const date = new Date();
    const now = date.toLocaleString();

    dispatch("add", {
      date: now,
    });
  };
</script>

<h2>Uso de "createEventDispatcher":</h2>

<!-- Si la propagación es más de 2 componentes puedes hacer esto. -->
<!-- Hará que se propague hasta el componente padre -->
<!-- <Button on:add /> -->
<button type="button" on:click={action}>Agrega una fecha</button>
