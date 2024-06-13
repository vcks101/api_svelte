<script>
    export let caracter;
</script>

<div class="subcard">
    <img src={caracter.imageUrl} alt={caracter.name} />
    <h2>{caracter.name}</h2>
    <h3>{caracter.films}</h3>
</div>
