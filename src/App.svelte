<!-- Funcionalidad de mi componente -->
<script>
  // importar componentes
  import Hi from "./lib/Hi.svelte";
  import User from "./lib/User.svelte";
  import Form from "./lib/Form.svelte";
  import Bind from "./lib/Bind.svelte";
  import Tasks from "./lib/Tasks.svelte";
  import Counter from "./lib/Counter.svelte";
  import AddDates from "./lib/AddDates.svelte";

  // Crear una prop
  let name = "Alfredo";

  // createEventDispatcher
  let count = 0;
  let dates = [];

  const message = (event) => {
    // Hay un parametro implicito llamado event.
    // El cual contiene toda la info del evento personalizado.
    console.log(event);

    const date = event.detail.date;
    // El = hace que se actualice el estado en Svelte.
    // Si hacemos un dates.psuh(date), no se actualiza el estado.
    dates = [...dates, date];
    count++;
  };
</script>

<!-- Directivas se pueden utlizar para inyectar elementos -->
<!--  <svelte:body /> <svelte:window /> -->
<!-- <svelte:head>
  <title>Hi</title>
</svelte:head> -->

<!-- Utilizar esos componentes -->
<main>
  <!-- Enviar una prop -->
  <Hi {name}>
    <h3 slot="title">Titulo Children</h3>
    <!-- Asi se usa un fragment en svelte -->
    <svelte:fragment slot="body">
      <p>Parrafo children</p>
      <p>Parrafo children</p>
    </svelte:fragment>
  </Hi>

  <Counter />
  <Form />
  <Tasks />
  <User />
  <Bind />

  <!-- Tiene la funcionalidad de utilizar el evento personalizado -->
  <AddDates on:add={message} />

  <h2 style="text-align:center">{count}</h2>

  {#each dates as d}
    <p>{d}</p>
  {:else}
    <p>No hay fechas</p>
  {/each}
</main>
