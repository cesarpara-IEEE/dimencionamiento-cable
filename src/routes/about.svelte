
<script>
	let ener = ""
	let v_inv = ""
	let v_bateria = ""
	let capasidad = ""
	let dop = ""

	$: b_serie = parseFloat(v_inv)/parseFloat(v_bateria)
	$: cap_total = parseFloat(ener)*1000/parseFloat(v_inv)
	$: b_paralelo = Math.ceil(cap_total / (parseFloat(capasidad) * parseFloat(dop)/100))

</script>

<svelte:head>
	<title>About</title>
</svelte:head>

<h1>Numero de baterias</h1>

<div class="entrada">
	<label for="">Energia que se proveera a la carga (KW-H)</label>
	<input type="text" bind:value={ener}>
	
	<label for="">Voltaje DC de entrada del banco de baterias al inversor</label>
	<input type="text" bind:value={v_inv}>
	
	<label for="">Voltaje de la bateria a utilizar</label>
	<input type="text" bind:value={v_bateria}>
	
	<label for="">Capacidad de la bateria a utilizar</label>
	<input type="text" bind:value={capasidad}>
	
	<label for="">Profundidad de descarga de la bateria (%)</label>
	<input type="text" bind:value={dop}>

	<label for="">Baterias en serie: {b_serie}</label>
	<label for="">Cantidad de paralelos: {b_paralelo}</label>
	<label for="">Numero de Baterias en total: {b_serie*b_paralelo}</label>

</div>



<style>
    .entrada{
        display: flex;
        flex-direction: column;
    }

</style>