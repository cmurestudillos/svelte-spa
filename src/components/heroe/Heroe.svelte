<script>
    import { onMount } from 'svelte';
    import { Link, useLocation } from 'svelte-routing';
    import customData from '../../data/heroes.json';
  
    export let nombre;
    let location = useLocation();
    let heroe = {};
  
    onMount(() => {
        getHeroe();
    });

    function getHeroe() {
      let heroeNombre = nombre || location.params.nombre;
      for (let index = 0; index < customData.length; index++) {
        if (heroeNombre === customData[index].nombre) {
          heroe = customData[index];
        }
      }
    }
  </script>
  
  <div class="bg-white shadow-lg p-3 mb-5 bg-white rounded">
    <h1 class="animated fadeIn slow">{heroe.nombre} <small>( {heroe.aparicion} )</small></h1>
    <hr>
    <div class="row animated fadeIn slow">
      <div class="col-md-4">
        <img src={`../${heroe.img}`} title={heroe.nombre} class="img-fluid shadow" alt={heroe.nombre} />
        <br><br>
        <Link to={'/'} class="btn btn-4 mt-2">Volver</Link>
      </div>
      <div class="col-md-8">
        <h3>{heroe.nombre}</h3>
        <hr>
        <p>{heroe.bio}</p>
        <div>
          {#if heroe.casa === 'DC'}
            <img src="../../../assets/img/dc.svg" title={heroe.casa} class="img-fluid" width="150" height="150" alt={heroe.casa} />
          {:else if heroe.casa === 'Marvel'}
            <img src="../../../assets/img/marvel.svg" title={heroe.casa} class="img-fluid" width="150" height="150" alt={heroe.casa} />
          {/if}
        </div>
      </div>
    </div>
  </div>
  
  <style>
    /* Estilos del componente Heroe */
  </style>
  