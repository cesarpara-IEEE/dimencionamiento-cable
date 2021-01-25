<script>
    let v_fuente = 0
    let v_caida = 0
    let metal = "al"
    let r_metal = 0
    let calibre = 8.40
    let longitud = 0
    let res_linea = 0
    let r_carga = 0

    const r_metales = {
        "al": 2.82,
        "cu": 1.7,
        "ag":1.59,
        "au":2.44
    }

    $: r_metal = r_metales[metal]
    $: res_linea = r_metal*Math.pow(10,-8)*parseFloat(longitud)/(parseFloat(calibre)*Math.pow(10,-6))
    $: v_caida = parseFloat(r_carga)*parseFloat(v_fuente)/(2*res_linea + parseFloat(r_carga))
</script>

<svelte:head>
    <title>Dimencion</title>
</svelte:head>

<h1>Dimencionamiento de lineas</h1>
<div class="entrada">
    <label for="">Voltaje de la fuente</label>
    <input type="text" bind:value={v_fuente}>
    <label for="">Resistitividad de la linea</label>
    <div class="seleccion">
        <label for="">Material: </label>
        <select bind:value={metal}>
            <option value="al">Aluminio</option>
            <option value="cu">Cobre</option>
            <option value="ag">Plata</option>
            <option value="au">Oro</option>
        </select>
        <label for="">Resistitividad:</label>
        <label for=""> {r_metal} x10^-8</label>
    </div>

    <div class="seleccion">
        <label for="">Diametro de la linea</label>
        <select bind:value={calibre}>
            <option value="8.40">8 AWG</option>
            <option value="13.30">6 AWG</option>
            <option value="21.15">4 AWG</option>
            <option value="33.62">2 AWG</option>
        </select>
    </div>
    <label for="">Longitud de la linea</label>
    <input bind:value={longitud}>
    <label for="">Resistencia de carga</label>
    <input bind:value={r_carga}>
    <label for="">La resistencia del cable es: {res_linea}</label>
    <label for="">La caida de tencion es: {v_caida}</label>
</div>

<style>
    .entrada{
        display: flex;
        flex-direction: column;
    }

    .seleccion{
        display: flex;
        flex-direction: row;
    }
</style>