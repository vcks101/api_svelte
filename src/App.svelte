<script>
  import Cards from "./lib/Cards.svelte";
  let caracteres = [];
  let pagina = 1;
  async function loadCharacter() {
    const response = await fetch(
      "https://api.disneyapi.dev/character?page=" + pagina,
    );
    const data = await response.json();
    console.log(data);
    console.log(data.data[0]);
    caracteres = data.data;
  }

  loadCharacter();

  function siguiente() {
    pagina++;
    loadCharacter();
  }

  function anterior() {
    pagina--;
    loadCharacter();
  }
</script>

<h1 class="title">Disney characters Svelte</h1>
<h2 class="title">Page: {pagina}</h2>

<div class="contenedor">
  <div class="botones">
    <button class="boton" on:click={anterior} disabled={pagina === 1}
      >Anterior</button
    >
    <button class="boton" on:click={siguiente}>Siguiente</button>
  </div>
  <div class="grid">
    {#each caracteres as caracter}
      <Cards {caracter} />
    {/each}
  </div>
</div>
