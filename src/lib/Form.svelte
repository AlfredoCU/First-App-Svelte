<!-- Eventos y reactividad -->
<script>
  // Crear estados
  let name = "";
  let lastname = "";
  let success = false;

  // Actualizar estados
  const onChangeName = ({ target }) => {
    name = target.value;
  };

  const onChangeLastname = ({ target }) => {
    lastname = target.value;
  };

  // Enivar estados
  const onSubmit = (event) => {
    // event.preventDefault();
    alert(`Hola ${name} ${lastname}`);
    success = true;
  };

  // Reactividad experta con el operador $
  let fullName;

  // Esto seria como un useEfect en React
  $: {
    fullName = `${name} ${lastname}`;
  }
</script>

<!-- Esto es un modificador de evento -->
<form on:submit|preventDefault={onSubmit}>
  <!-- Se utiliza keyup -->
  <label for="name">
    Nombre:
    <input
      type="text"
      name="name"
      placeholder="Nombre"
      on:keyup={onChangeName}
    />
  </label>

  <label for="lastname">
    Apellidos:
    <input
      type="text"
      name="lastname"
      placeholder="Apellido"
      on:keyup={onChangeLastname}
    />
  </label>

  <!-- Condicionales en información -->
  <div class="info">
    <h2>Información agregada:</h2>
    <p>Nombre: {name || "N/A"}</p>
    <p>Apellidos: {lastname || "N/A"}</p>
  </div>

  <!-- Condicionales en botón -->
  <button type="submit" disabled={!name || !lastname}>Enviar</button>
</form>

<!-- if else -->
{#if success}
  <p>La información se a enviado!</p>
{:else}
  <p>Esperando información...</p>
{/if}

<h3>{fullName?.length > 1 ? fullName : "No hay nombre"}</h3>

<style>
  .info {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
  }

  .info > p {
    margin: 0;
  }

  button {
    width: 100%;
    margin-top: 1rem;
  }
</style>
