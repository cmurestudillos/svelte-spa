<script>
    import { Link } from 'svelte-routing';
    import customData from '../../../data/heroes.json';
  
    let heroes = customData;
  </script>

  <div class="container mt-4">
    <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-4">
      {#each heroes as heroe (heroe.nombre)}
        <div class="col p-1">
          <div class="card h-100 shadow animated fadeIn slow m-2">
            <img src={heroe.img} alt={heroe.nombre} class="card-img-top img-fluid" />
            <div class="card-body">
              <h5 class="card-title">{heroe.nombre}</h5>
              <p class="card-text">{heroe.bio}</p>
              <small class="text-muted"><strong>Año:</strong> {heroe.aparicion}</small>
            </div>
            <div class="card-footer">
              <Link to={`/heroe/${heroe.nombre}`} class="btn btn-4 mt-2">Ver mas...</Link>
            </div>
          </div>
        </div>
      {/each}
    </div>
  </div>
  
  <style>
    /* Estilos del componente Card */
  </style>
  