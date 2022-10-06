<script>
  const userData = async () => {
    const url = "https://randomuser.me/api/";
    const res = await fetch(url);
    const data = res.json();
    return data;
  };
</script>

<div>
  <h2>Información del usuario:</h2>
  {#await userData()}
    <p>Esperando resultados...</p>
  {:then data}
    <p><b>UserName:</b> {data.results[0].login.username}</p>
    <p><b>Email:</b> {data.results[0].email}</p>
    <p><b>Phone:</b> {data.results[0].phone}</p>
  {:catch}
    <p>Hay un error con su petición</p>
  {/await}
</div>

<style>
  div {
    text-align: left;
  }

  p {
    margin: 0;
  }
</style>
