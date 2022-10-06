<!-- Funcionalidad de mi componente -->
<script>
  // Recibir una prop
  export let name;
</script>

<!-- Mi componente -->
<h1 class="title">Hola Mundo</h1>
<!-- No es necesario una etiqueta padre que englobe todas las etiquetas -->
<p>Mi primera aplicación en Svelte</p>
<p class="me">Página web creado por <em>{name}</em></p>

<!-- Esto es como un children -->
<!-- <slot>
  <p>Parrafo por defecto</p>
</slot> -->

<!-- Si necesitas más childrens -->
<slot name="title">
  <h1>Titulo por defecto</h1>
</slot>

<slot name="body">
  <p>Parrafo por defecto</p>
</slot>

<!-- Estilos unicamente para mi componente -->
<style>
  .title {
    font-weight: 300;
  }

  .me {
    margin: 0;
    font-size: 12px;
  }
</style>
