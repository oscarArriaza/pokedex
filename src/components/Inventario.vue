<template>
    <Tienda id="tienda" hidden @cerrar-tienda="cerrarTienda" @actualizar-inventario="actualizarInventario" :inventario="{'duskBall':`${inventarioDos.duskBall}`,'greatBall':`${inventarioDos.greatBall}`,'healBall':`${inventarioDos.healBall}`,'masterBall':`${inventarioDos.masterBall}`,'repeatBall':`${inventarioDos.repeatBall}`,'pocion':`${inventarioDos.pocion}`,'antidoto':`${inventarioDos.antidoto}`}"></Tienda>
    <div id="inventario" class="modal-dialog modal-dialog-centered">
        <div class="modal-content">
          <div class="modal-header">
              <h3 class="text-center" id="modalInventarioLabel">
                Inventario
              </h3>
          </div>
          <div class="modal-body" style="height: 353px; overflow-y: auto;">
            <div class="row">
                <p class="h5 text-center col-sm-12">Pokeballs</p>
                <div class="col-sm-12 col-md-6 mb-1" style="display:flex; align-items: center;">
                    <img src="../../media/imagenes/dusk-ball.png" alt="Imagen de una dusk ball" width="130" draggable="false">
                    <div>
                        <div class="text-center bg-primary">
                            <span>
                                Dusk ball
                            </span>
                        </div>
                        <div>
                            <small>
                                Cantidad:<strong id="cantidadDuskBalls" class="text-warning">{{inventario.duskBall}}</strong>
                            </small>
                        </div>
                    </div>
                </div>
                <div class="col-sm-12 col-md-6 mb-1" style="display:flex; align-items: center;">
                    <img src="../../media/imagenes/great-ball.png" alt="Imagen de una great ball" width="130" draggable="false">
                    <div>
                        <div class="text-center bg-primary">
                            <span>
                                Great ball
                            </span>
                        </div>
                        <div>
                            <small>
                                Cantidad:<strong id="cantidadGreatBalls" class="text-warning">{{inventarioDos.greatBall}}</strong>
                            </small>
                        </div>
                    </div>
                </div>
                <div class="col-sm-12 col-md-6 mb-1" style="display:flex; align-items: center;">
                    <img src="../../media/imagenes/heal-ball.png" alt="Imagen de una heal ball" width="130" draggable="false">
                    <div>
                        <div class="text-center bg-primary">
                            <span>
                                Heal ball
                            </span>
                        </div>
                        <div>
                            <small>
                                Cantidad:<strong id="cantidadHealBalls" class="text-warning">{{inventarioDos.healBall}}</strong>
                            </small>
                        </div>
                    </div>
                </div>
                <div class="col-sm-12 col-md-6 mb-1" style="display:flex; align-items: center;">
                    <img src="../../media/imagenes/master-ball.png" alt="Imagen de una master ball" width="130" draggable="false">
                    <div>
                        <div class="text-center bg-primary">
                            <span>
                                Master ball
                            </span>
                        </div>
                        <div>
                            <small>
                                Cantidad:<strong id="cantidadMasterBalls" class="text-warning">{{inventarioDos.masterBall}}</strong>
                            </small>
                        </div>
                    </div>
                </div>
                <div class="col-sm-12 col-md-6 mb-1" style="display:flex; align-items: center;">
                    <img src="../../media/imagenes/repeat-ball.png" alt="Imagen de una repeat ball" width="130" draggable="false">
                    <div>
                        <div class="text-center bg-primary">
                            <span>
                                Repeat ball
                            </span>
                        </div>
                        <div>
                            <small>
                                Cantidad:<strong id="cantidadRepeatBalls" class="text-warning">{{inventarioDos.repeatBall}}</strong>
                            </small>
                        </div>
                    </div>
                </div>
                <p class="h5 text-center col-sm-12">Pociones</p>
                <div class="col-sm-12 col-md-6 mb-1" style="display:flex; align-items: center;">
                    <img src="../../media/imagenes/pocion.png" alt="Imagen de una pocion" width="130" draggable="false">
                    <div>
                        <div class="text-center bg-primary">
                            <span>
                                Pocion
                            </span>
                        </div>
                        <div>
                            <small>
                                Cantidad:<strong id="cantidadPociones" class="text-warning">{{inventarioDos.pocion}}</strong>
                            </small>
                        </div>
                    </div>
                </div>
                <p class="h5 text-center col-sm-12">Antidotos</p>
                <div class="col-sm-12 col-md-6 mb-1" style="display:flex; align-items: center;">
                    <img src="../../media/imagenes/antidoto.png" alt="Imagen de un antidoto" width="130" draggable="false">
                    <div>
                        <div class="text-center bg-primary">
                            <span>
                                Antidoto
                            </span>
                        </div>
                        <div>
                            <small>
                                Cantidad:<strong id="cantidadAntidotos" class="text-warning">{{inventario.antidoto}}</strong>
                            </small>
                        </div>
                    </div>
                </div>
            </div>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" id="botonCerrarModalInventario" data-bs-dismiss="modal">
              Atras
            </button>
            <button type="button" class="btn btn-primary" @click="abrirTienda()">
              Tienda
            </button>
          </div>
        </div>
    </div>
</template>

<script>
    import Tienda from './Tienda.vue'
    export default {
        data(){
            return {
                inventarioDos:{}
            }
        },
        methods: {
            copiarInventario()
            {
                this.inventarioDos = this.inventario;
            },
            abrirTienda()
            {
                let inventario = document.getElementById('inventario');
                inventario.setAttribute('hidden', "true");
                let tienda = document.getElementById('tienda');
                tienda.removeAttribute('hidden');
            },
            cerrarTienda()
            {
                let inventario = document.getElementById('inventario');
                inventario.removeAttribute('hidden');
                let tienda = document.getElementById('tienda');
                tienda.setAttribute('hidden', "true");
            },
            actualizarInventario(inventarioActualizado)
            {
                this.inventarioDos.duskBall = inventarioActualizado.duskBall;
                this.inventarioDos.greatBall = inventarioActualizado.greatBall;
                this.inventarioDos.healBall = inventarioActualizado.healBall;
                this.inventarioDos.masterBall = inventarioActualizado.masterBall;
                this.inventarioDos.repeatBall = inventarioActualizado.repeatBall;
                this.inventarioDos.pocion = inventarioActualizado.pocion;
                this.inventarioDos.antidoto = inventarioActualizado.antidoto;

                let cantidadDuskBalls = document.getElementById('cantidadDuskBalls');
                cantidadDuskBalls.textContent="";
                cantidadDuskBalls.textContent=inventarioActualizado.duskBall;

                let cantidadGreatBalls = document.getElementById('cantidadGreatBalls');
                cantidadGreatBalls.textContent="";
                cantidadGreatBalls.textContent=inventarioActualizado.greatBall;

                let cantidadHealBalls = document.getElementById('cantidadHealBalls');
                cantidadHealBalls.textContent="";
                cantidadHealBalls.textContent=inventarioActualizado.healBall;

                let cantidadMasterBalls = document.getElementById('cantidadMasterBalls');
                cantidadMasterBalls.textContent="";
                cantidadMasterBalls.textContent=inventarioActualizado.masterBall;

                let cantidadRepeatBalls = document.getElementById('cantidadRepeatBalls');
                cantidadRepeatBalls.textContent="";
                cantidadRepeatBalls.textContent=inventarioActualizado.repeatBall;

                let cantidadPociones = document.getElementById('cantidadPociones');
                cantidadPociones.textContent="";
                cantidadPociones.textContent=inventarioActualizado.pocion;

                let cantidadAntidotos = document.getElementById('cantidadAntidotos');
                cantidadAntidotos.textContent="";
                cantidadAntidotos.textContent=inventarioActualizado.antidoto;
            }

        },
        components: {
            Tienda
        },
        props: {
            inventario: Object
        },
        created(){
            this.copiarInventario();
        },
    }
</script>

<style>
    
</style>