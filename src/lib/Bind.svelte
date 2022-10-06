<!-- Bind nos ayuda a crear eventos y actualizar el estado de una forma más limpia -->
<script>
  // Para usar TypeScript en lugar de JavaScript es necesario utilizar lang
  // <script lang="ts">

  // Los estados
  let nickname = "Spartan 117";
  let status = true;
  let country = "México";
  let input;

  // Lista de países
  let countries = [
    "México",
    "Japon",
    "Estados Unidos",
    "Corea del Sur",
    "Holanda",
  ];

  // se obtine referencia del DOM con bind:this y de esta forma manipular el DOM.
  const focus = () => {
    if (input) {
      input.focus();
    }
  };
</script>

<h2>Uso del bind:</h2>

<label for="nickname">
  NickName:
  <input type="text" name="nickname" bind:value={nickname} />
</label>

<div class="check">
  <input class="checkbox" type="checkbox" name="status" bind:checked={status} />
  <span>Estado</span>
</div>

<label for="country">
  NickName:
  <select name="country" bind:value={country}>
    {#each countries as c}
      <option value={c}>{c}</option>
    {/each}
  </select>
</label>

<div class="info">
  <p><b>El nickname:</b> {nickname}</p>
  <p>
    <b>El estado:</b>
    <!-- Se pueden crear validaciones de estilado -->
    <span class={status ? "green" : "red"}>
      {status ? "Activo" : "No Activo"}
    </span>
  </p>
  <p><b>El país:</b> {country}</p>
</div>

<h2>Uso del bind:this:</h2>

<label for="search">
  Buscar:
  <input type="text" name="search" placeholder="Buscar" bind:this={input} />

  <button type="button" on:click={focus}>Buscar</button>
</label>

<!-- Se puede usar estilos de linea -->
<!-- style="color: blue;" -->

<!-- se pueden enviar variables en los estilos de linea -->
<!-- Y crear un comportamiento como Style Componentes y sus props -->
<div class="content" style:--bg-color="orange">
  <p>Prueba de estilos de linea y variables</p>
</div>

<!-- Para utilizar scss en lugar de css es necesario utilizar lang -->

<!-- <style lang="scss"> -->
<style>
  h2 {
    text-align: left;
  }

  /* Se pueden crear estilos globales, pero no es recomendable */
  /* Es mejor realizar hojas de estilo e importarlas directamente en el App */
  /* De esa forma importamos los estilos globales desde el App y evitamos caos */
  /* En buscar los estilos globales desde cualquier otro component */
  :global(label) {
    width: 100%;
    display: flex;
    margin: 1rem 0;
    flex-direction: column;
    align-items: flex-start;
  }

  :global(input, select) {
    width: 95%;
    padding: 0.5rem;
    box-sizing: content-box;
    width: -webkit-fill-available;
  }

  .check {
    gap: 0.5rem;
    display: flex;
    justify-content: flex-start;
    align-items: initial;
  }

  .checkbox {
    width: auto;
  }

  input[type="checkbox"] {
    zoom: 1.3;
  }

  .green {
    color: greenyellow;
  }

  .red {
    color: red;
  }

  .content {
    background-color: var(--bg-color);
  }

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
