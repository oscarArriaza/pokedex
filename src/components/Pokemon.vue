<template>
    <div class="modal fade" id="modalAlertaEquipoCompleto" data-bs-backdrop="static" data-bs-keyboard="false" tabindex="-1" aria-labelledby="modalPedidoLabel" aria-hidden="true">
      <div class="modal-dialog modal-dialog-centered">
        <div class="modal-content">
          <div class="modal-header">
              <h1 class="modal-title fs-5" id="modalAlertaEquipoCompletoLabel">
                Alerta
              </h1>
          </div>
          <div class="modal-body">
            <p>
                "No puedes tener más de 6 pokemons en tu equipo."
            </p>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" id="botonCerrarModalAlertaEquipoCompleto" data-bs-dismiss="modal">
              Atras
            </button>
          </div>
        </div>
      </div>
    </div>
    <div class="modal fade" id="modalAlertaFavoritos" data-bs-backdrop="static" data-bs-keyboard="false" tabindex="-1" aria-labelledby="modalPedidoLabel" aria-hidden="true">
      <div class="modal-dialog modal-dialog-centered">
        <div class="modal-content">
          <div class="modal-header">
              <h1 class="modal-title fs-5" id="modalAlertaFavoritosLabel">
                Alerta
              </h1>
          </div>
          <div class="modal-body">
            <p>
                "No se puede mostrar, no hay pokemons en favoritos."
            </p>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" id="botonCerrarmodalAlertaFavoritos" data-bs-dismiss="modal">
              Atras
            </button>
          </div>
        </div>
      </div>
    </div>
    <div class="modal fade" id="modalAlertaEquipoIncompleto" data-bs-backdrop="static" data-bs-keyboard="false" tabindex="-1" aria-labelledby="modalPedidoLabel" aria-hidden="true">
      <div class="modal-dialog modal-dialog-centered">
        <div class="modal-content">
          <div class="modal-header">
              <h1 class="modal-title fs-5" id="modalAlertaEquipoIncompletoLabel">
                Alerta
              </h1>
          </div>
          <div class="modal-body">
            <p>
                "No se puede mostrar debes tener 6 pokemons en tu equipo."
            </p>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" id="botonCerrarModalAlertaEquipoIncompleto" data-bs-dismiss="modal">
              Atras
            </button>
          </div>
        </div>
      </div>
    </div>
    <div class="modal fade" id="modalInventario" data-bs-backdrop="static" data-bs-keyboard="false" tabindex="-1" aria-labelledby="modalPedidoLabel" aria-hidden="true">
        <Inventario :inventario="{'duskBall':`${inventario.duskBall}`,'greatBall':`${inventario.greatBall}`,'healBall':`${inventario.healBall}`,'masterBall':`${inventario.masterBall}`,'repeatBall':`${inventario.repeatBall}`,'pocion':`${inventario.pocion}`,'antidoto':`${inventario.antidoto}`}"></Inventario>
    </div>
    <header style="height: 103px;">
      <nav class="navbar navbar-expand-lg bg-dark fixed-top" data-bs-theme="dark">
        <div class="container-fluid">
          <a class="navbar-brand">
            <img src="/media/imagenes/pokeball.png" alt="Imagen de una pokeball" width="60vw" height="60vh" class="d-inline-block align-top" draggable="false">
          </a>
          <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarColor02" aria-controls="navbarColor02" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarColor02">
            <ul class="navbar-nav me-auto">
              <li class="nav-item centrar">
                <a class="nav-link elementoCliqueable" @click="mostrarTodos()" id="mostrarTodos">Todos
                  <!--<span class="visually-hidden">(current)</span>-->
                </a>
              </li>
              <li class="nav-item centrar">
                <a class="nav-link elementoCliqueable" @click="mostrarSoloLosFavoritos()">Favoritos</a>
              </li>
              <li class="nav-item centrar">
                <a class="nav-link elementoCliqueable" @click="mostrarEquipo()">Equipo</a>
              </li>
              <li class="nav-item centrar">
                <a class="nav-link elementoCliqueable" data-bs-toggle="modal" data-bs-target="#modalInventario">Inventario</a>
              </li>
              <li class="nav-item dropdown centrar">
                <a class="nav-link dropdown-toggle" data-bs-toggle="dropdown" role="button" aria-haspopup="true" aria-expanded="false">Buscar por tipo</a>
                <div class="dropdown-menu" style="height: 200px; overflow-y: auto;">
                    <template v-for="tipo in tipos">
                        <a class="dropdown-item elementoCliqueable" @click="buscarPorTipo($event.target.textContent)">{{tipo}}</a>
                    </template>
                </div>
              </li>
              <li>
                <a class="nav-link elementoCliqueable">
                    <Rango @intervalo="mostrarSegunElRango"></Rango>
                </a>
                <!--<div class="container">
                    <div class="slider-container">
                        <label for="volumeSlider" class="form-label">Volumen</label>
                        <input type="range" class="form-range slider" id="volumeSlider" min="0" max="100" step="1">
                    </div>
                </div>-->
              </li>
            </ul>
          </div>
        </div>
      </nav>
    </header>
    <section class="container-fluid">
        <p class="h5 text-center">
            Pokemons
        </p>
        <div class="row">
            <template v-for="pokemonId in pokemonsId">
                <div v-if="favoritos.includes(pokemonId)" class="col-sm-12 col-md-6 col-lg-4 col-xl-3 mb-4 carta favorito">
                    <div class="card border-primary">
                        <div class="card-header">
                            <h5 class="card-title">
                                {{pokemons[pokemonId-1].name}}
                            </h5>
                        </div>
                        <div class="card-body">
                            <img class="w-100" :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/${pokemonId}.png`" :alt="`Imagen de ${pokemons[pokemonId-1].name}`" draggable="false">
                            <div>
                                <p class="numero" :data-numero="`${pokemonId}`">
                                    Nro. {{pokemonId}}
                                </p>
                                <p class="tipo">
                                    Tipos:
                                    <span v-for="pokemonTipos in pokemonsTipos[pokemonId-1]">
                                        {{pokemonTipos.type.name}},
                                    </span>
                                </p>
                                <div class="form-check form-switch">
                                    <label class="form-check-label" for="flexSwitchCheckChecked">Añadir a favoritos</label>
                                    <input class="form-check-input" type="checkbox" role="switch" id="flexSwitchCheckChecked" @click="agregarAFavoritos(pokemonId,$event.target)" :checked="favoritos.includes(pokemonId)">
                                </div>
                                <div class="form-check form-switch">
                                    <label class="form-check-label" for="flexSwitchCheckChecked">Añadir al equipo</label>
                                    <input class="form-check-input equipo" type="checkbox" role="switch" id="flexSwitchCheckChecked" @click="agregarAlEquipo(pokemonId,$event.target)" :checked="equipo.includes(pokemonId)">
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div v-else-if="favoritos.includes(pokemonId) && equipo.includes(pokemonId)" class="col-sm-12 col-md-6 col-lg-4 col-xl-3 mb-4 carta favorito equipo">
                    <div class="card border-primary">
                        <div class="card-header">
                            <h5 class="card-title">
                                {{pokemons[pokemonId-1].name}}
                            </h5>
                        </div>
                        <div class="card-body">
                            <img class="w-100" :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/${pokemonId}.png`" :alt="`Imagen de ${pokemons[pokemonId-1].name}`" draggable="false">
                            <div>
                                <p class="numero" :data-numero="`${pokemonId}`">
                                    Nro. {{pokemonId}}
                                </p>
                                <p class="tipo">
                                    Tipos:
                                    <span v-for="tipo in pokemonsTipos[pokemonId-1]">
                                        {{tipo.type.name}},
                                    </span>
                                </p>
                                <div class="form-check form-switch">
                                    <label class="form-check-label" for="flexSwitchCheckChecked">Añadir a favoritos</label>
                                    <input class="form-check-input" type="checkbox" role="switch" id="flexSwitchCheckChecked" @click="agregarAFavoritos(pokemonId,$event.target)" :checked="favoritos.includes(pokemonId)">
                                </div>
                                <div class="form-check form-switch">
                                    <label class="form-check-label" for="flexSwitchCheckChecked">Añadir al equipo</label>
                                    <input class="form-check-input equipo" type="checkbox" role="switch" id="flexSwitchCheckChecked" @click="agregarAlEquipo(pokemonId,$event.target)" :checked="equipo.includes(pokemonId)">
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div v-else-if="equipo.includes(pokemonId)" class="col-sm-12 col-md-6 col-lg-4 col-xl-3 mb-4 carta equipo">
                    <div class="card border-primary">
                        <div class="card-header">
                            <h5 class="card-title">
                                {{pokemons[pokemonId-1].name}}
                            </h5>
                        </div>
                        <div class="card-body">
                            <img class="w-100" :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/${pokemonId}.png`" :alt="`Imagen de ${pokemons[pokemonId-1].name}`" draggable="false">
                            <div>
                                <p class="numero" :data-numero="`${pokemonId}`">
                                    Nro. {{pokemonId}}
                                </p>
                                <p class="tipo">
                                    Tipos:
                                    <span v-for="tipo in pokemonsTipos[pokemonId-1]">
                                        {{tipo.type.name}},
                                    </span>
                                </p>
                                <div class="form-check form-switch">
                                    <label class="form-check-label" for="flexSwitchCheckChecked">Añadir a favoritos</label>
                                    <input class="form-check-input" type="checkbox" role="switch" id="flexSwitchCheckChecked" @click="agregarAFavoritos(pokemonId,$event.target)" :checked="favoritos.includes(pokemonId)">
                                </div>
                                <div class="form-check form-switch">
                                    <label class="form-check-label" for="flexSwitchCheckChecked">Añadir al equipo</label>
                                    <input class="form-check-input equipo" type="checkbox" role="switch" id="flexSwitchCheckChecked" @click="agregarAlEquipo(pokemonId,$event.target)" :checked="equipo.includes(pokemonId)">
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div v-else class="col-sm-12 col-md-6 col-lg-4 col-xl-3 mb-4 carta">
                    <div class="card border-primary">
                        <div class="card-header">
                            <h5 class="card-title">
                                {{pokemons[pokemonId-1].name}}
                            </h5>
                        </div>
                        <div class="card-body">
                            <img class="w-100" :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/${pokemonId}.png`" :alt="`Imagen de ${pokemons[pokemonId-1].name}`" draggable="false">
                            <div>
                                <p class="numero" :data-numero="`${pokemonId}`">
                                    Nro. {{pokemonId}}
                                </p>
                                <p class="tipo">
                                    Tipos:
                                    <span v-for="tipo in pokemonsTipos[pokemonId-1]">
                                        {{tipo.type.name}},
                                    </span>
                                </p>
                                <div class="form-check form-switch">
                                    <label class="form-check-label" for="flexSwitchCheckChecked">Añadir a favoritos</label>
                                    <input class="form-check-input" type="checkbox" role="switch" id="flexSwitchCheckChecked" @click="agregarAFavoritos(pokemonId,$event.target)" :checked="favoritos.includes(pokemonId)">
                                </div>
                                <div class="form-check form-switch">
                                    <label class="form-check-label" for="flexSwitchCheckChecked">Añadir al equipo</label>
                                    <input class="form-check-input equipo" type="checkbox" role="switch" id="flexSwitchCheckChecked" @click="agregarAlEquipo(pokemonId,$event.target)" :checked="equipo.includes(pokemonId)">
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </template>

            <!--<div v-for="pokemonTipo in  pokemonsTipos" class="alert alert-primary col-sm-12 mb-3 modulo">
                {{pokemonTipo}}
            </div>-->
        </div>
        <input id="botonDesplegarModalAlertaEquipoCompleto" type="button" data-bs-toggle="modal" data-bs-target="#modalAlertaEquipoCompleto" hidden>
        <input id="botonDesplegarModalAlertaFavoritos" type="button" data-bs-toggle="modal" data-bs-target="#modalAlertaFavoritos" hidden>
        <input id="botonDesplegarModalAlertaEquipoIncompleto" type="button" data-bs-toggle="modal" data-bs-target="#modalAlertaEquipoIncompleto" hidden>
    </section>
    <footer class="bg-primary" id="contenedorFooter" style="display:flex; justify-content: center;">
      <a href="https://politecnics.barcelona/" target="_blank">
        <img src="/media/imagenes/logo_politecnics.png" alt="Logo del politecnics" style="width:22vw; height:12vh;" draggable="false">
      </a>
      <div class="ms-1" style="display:flex; align-items: center; justify-content: center;">
        "Todos los derechos reservados."
      </div>
    </footer>
</template>


<script>
    import axios from 'axios'
    import Rango from './Rango.vue'
    import Inventario from './Inventario.vue'

    export default {
        data(){
            return {
                pokemonsId:[],
                pokemons:[],
                pokemonsTipos:[],
                favoritos:[],
                equipo:[],
                tipos:[],
                inventario:{}
            }
        },
        methods: {
            obtenerFavoritos()
            {
                try
                {
                    let favoritos;
                    let datosJSON = localStorage.getItem('datosFavoritos');
                    let datos = JSON.parse(datosJSON);
                    favoritos=datos.favoritos;
                    this.favoritos=favoritos;
                }
                catch (error)
                {
                    let datos=
                    {
                        favoritos: []
                    }
                    let datosJSON=JSON.stringify(datos);
                    localStorage.setItem('datosFavoritos',datosJSON);
                }
                this.obtenerEquipo()
            },
            obtenerEquipo()
            {
                try
                {
                    let equipo;
                    let datosJSON = localStorage.getItem('datosEquipo');
                    let datos = JSON.parse(datosJSON);
                    equipo=datos.equipo;
                    this.equipo=equipo;
                }
                catch (error)
                {
                    let datos=
                    {
                        equipo: []
                    }
                    let datosJSON=JSON.stringify(datos);
                    localStorage.setItem('datosEquipo',datosJSON);
                }
                this.obtenerInventario()
            },
            obtenerInventario()
            {
                try
                {
                    let inventario;
                    let datosJSON = localStorage.getItem('datosInventario');
                    let datos = JSON.parse(datosJSON);
                    inventario=datos.inventario;
                    this.inventario=inventario;
                }
                catch (error)
                {
                    let datos=
                    {
                        inventario:{duskBall:0,greatBall:0,healBall:0,masterBall:0,repeatBall:0,pocion:0,antidoto:0}
                    }
                    let datosJSON=JSON.stringify(datos);
                    localStorage.setItem('datosInventario',datosJSON);
                    this.inventario=datos.inventario;
                }
                this.obtenerIdYNombresPokemons()
            },
            obtenerIdYNombresPokemons()
            {
                const me=this
                axios
                    .get("https://pokeapi.co/api/v2/pokemon/?offset=0&limit=151")
                    .then(response=>{
                        me.pokemons=response.data.results
                        me.pokemonsId=response.data.results.map(pokemon=>pokemon.url.split('/')[6])
                        me.obtenerTiposPokemons()
                    })
                    .catch(error=>{

                    })
            },
            /*obtenerTiposPokemons()
            {
                const me=this
                for (let i = 0; i <me.pokemonsId.length; i++) {
                    axios
                        .get("https://pokeapi.co/api/v2/pokemon/"+me.pokemonsId[i]+"/")
                        .then(response=>{
                            //console.log(response.data.types)
                            me.pokemonsTipos.push(response.data.types)
                            //console.log(me.pokemonsTipos.length);
                        })
                        .catch(error=>{

                        })
                }
                console.log(me.pokemonsTipos)
            },*/
            async obtenerTiposPokemons()
            {
                const me = this;
                try
                {
                    for (let i = 0; i < me.pokemonsId.length; i++)
                    {
                        const response = await axios.get(`https://pokeapi.co/api/v2/pokemon/${me.pokemonsId[i]}/`);
                        me.pokemonsTipos.push(response.data.types);
                    }
                    me.obtenerTipos();
                }
                catch (error)
                {
                    console.error("Error al obtener tipos de Pokémon:", error);
                }
            },
            obtenerTipos()
            {
                const me=this
                axios
                    .get("https://pokeapi.co/api/v2/type")
                    .then(response=>{
                        me.tipos=response.data.results.map(tipo=>tipo.name)
                    })
                    .catch(error=>{

                    })
            },
            agregarAFavoritos(pokemonId,checkbox)
            {
                let carta = checkbox.closest('.carta');
                if(this.favoritos.includes(pokemonId))
                {
                    this.favoritos=this.favoritos.filter(favorito=>favorito!=pokemonId);
                    carta.classList.remove('favorito');
                }
                else
                {
                    this.favoritos.push(pokemonId)
                    carta.classList.add('favorito');
                }
                let datos=
                {
                    favoritos: this.favoritos
                }
                let datosJSON=JSON.stringify(datos);
                localStorage.setItem('datosFavoritos',datosJSON);
            },
            agregarAlEquipo(pokemonId,checkbox)
            {
                let carta = checkbox.closest('.carta');
                if(this.equipo.length>=6 && !this.equipo.includes(pokemonId))
                {
                    checkbox.checked=false
                    //alert("No puedes tener más de 6 pokemons en tu equipo.")
                    let botonDesplegarModalAlertaEquipoCompleto=document.getElementById('botonDesplegarModalAlertaEquipoCompleto')
                    botonDesplegarModalAlertaEquipoCompleto.click()
                    return
                }
                else
                {
                    if(this.equipo.includes(pokemonId))
                    {
                        this.equipo=this.equipo.filter(miembroEquipo=>miembroEquipo!=pokemonId)
                        carta.classList.remove('equipo');
                    }
                    else
                    {
                        this.equipo.push(pokemonId)
                        carta.classList.add('equipo');
                    }
                    let datos=
                    {
                        equipo: this.equipo
                    }
                    let datosJSON=JSON.stringify(datos);
                    localStorage.setItem('datosEquipo',datosJSON);
                }
            },
            mostrarTodos()
            {
                let cartas = document.getElementsByClassName('carta');
                for (let i = 0; i < cartas.length; i++)
                {
                    cartas[i].style.display='block';
                }
            },
            mostrarSoloLosFavoritos()
            {
                if(this.favoritos.length==0)
                {
                    let botonDesplegarModalAlertaFavoritos=document.getElementById('botonDesplegarModalAlertaFavoritos');
                    botonDesplegarModalAlertaFavoritos.click();
                    return
                }
                else
                {
                    let cartas = document.getElementsByClassName('carta');
                    for (let i = 0; i < cartas.length; i++)
                    {
                        if(cartas[i].classList.contains('favorito'))
                        {
                            cartas[i].style.display='block';
                        }
                        else
                        {
                            cartas[i].style.display='none';
                        }
                    }
                }
            },
            mostrarEquipo()
            {
                if(this.equipo.length<6)
                {
                    let botonDesplegarModalAlertaEquipoIncompleto=document.getElementById('botonDesplegarModalAlertaEquipoIncompleto')
                    let mostrarTodos=document.getElementById('mostrarTodos');
                    botonDesplegarModalAlertaEquipoIncompleto.click();
                    mostrarTodos.click();
                    return;
                }
                else
                {
                    let cartas = document.getElementsByClassName('carta');
                    for (let i = 0; i < cartas.length; i++)
                    {
                        if(cartas[i].classList.contains('equipo'))
                        {
                            cartas[i].style.display='block';
                        }
                        else
                        {
                            cartas[i].style.display='none';
                        }
                    }
                }
            },
            buscarPorTipo(tipo)
            {
                let parrafosTipos=document.getElementsByClassName('tipo');
                for (let i = 0; i < parrafosTipos.length; i++)
                {
                    //console.log(parrafosTipos[i].textContent)
                    if(parrafosTipos[i].textContent.includes(tipo))
                    {
                        parrafosTipos[i].closest('.carta').style.display='block';
                    }
                    else
                    {
                        parrafosTipos[i].closest('.carta').style.display='none';
                    }
                }
                /*let cartas = document.getElementsByClassName('carta');
                for (let i = 0; i < cartas.length; i++)
                {
                    if(cartas[i].querySelector('.tipo').textContent.includes(tipo))
                    {
                        cartas[i].style.display='block';
                    }
                    else
                    {
                        cartas[i].style.display='none';
                    }
                }*/
                //console.log(tipo)
            },
            mostrarSegunElRango(intervalo)
            {
                let parrafosNumero=document.getElementsByClassName('numero');

                for (let i = 0; i < parrafosNumero.length; i++)
                {
                    //console.log(parrafosNumero[i].getAttribute('data-numero'))
                    if(Number(parrafosNumero[i].getAttribute('data-numero'))>=Number(intervalo[0]) && Number(parrafosNumero[i].getAttribute('data-numero'))<=Number(intervalo[1]))
                    {
                        parrafosNumero[i].closest('.carta').style.display='block';
                    }
                    else
                    {
                        parrafosNumero[i].closest('.carta').style.display='none';
                    }
                }
                //console.log(intervalo);
            }
        },
        components: {
            Rango,
            Inventario
        },
        created(){
            this.obtenerFavoritos()
        },
    }
</script>


<style>
    .elementoCliqueable
    {
        cursor: pointer;
    }
    .centrar
    {
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>