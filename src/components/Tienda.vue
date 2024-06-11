<template>
    <div class="modal-dialog modal-dialog-centered">
        <div class="modal-content">
            <div class="modal-header">
                <p class="h3 text-center" id="modalTiendaLabel">
                    Tienda
                </p>
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
                                <div class="centrar">
                                    <button type="button" class="btn btn-danger btn-sm me-1" @click="quitar($event.target)">
                                        -
                                    </button>
                                    <span id="spanDuskBall" class="me-1">0</span>
                                    <button type="button" class="btn btn-success btn-sm" @click="aniadir($event.target)">
                                        +
                                    </button>
                                </div>
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
                                <div class="centrar">
                                    <button type="button" class="btn btn-danger btn-sm me-1" @click="quitar($event.target)">
                                        -
                                    </button>
                                    <span id="spanGreatBall" class="me-1">0</span>
                                    <button type="button" class="btn btn-success btn-sm" @click="aniadir($event.target)">
                                        +
                                    </button>
                                </div>
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
                                <div class="centrar">
                                    <button type="button" class="btn btn-danger btn-sm me-1" @click="quitar($event.target)">
                                        -
                                    </button>
                                    <span id="spanHealBall" class="me-1">0</span>
                                    <button type="button" class="btn btn-success btn-sm" @click="aniadir($event.target)">
                                        +
                                    </button>
                                </div>
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
                                <div class="centrar">
                                    <button type="button" class="btn btn-danger btn-sm me-1" @click="quitar($event.target)">
                                        -
                                    </button>
                                    <span id="spanMasterBall" class="me-1">0</span>
                                    <button type="button" class="btn btn-success btn-sm" @click="aniadir($event.target)">
                                        +
                                    </button>
                                </div>
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
                                <div class="centrar">
                                    <button type="button" class="btn btn-danger btn-sm me-1" @click="quitar($event.target)">
                                        -
                                    </button>
                                    <span id="spanRepeatBall" class="me-1">0</span>
                                    <button type="button" class="btn btn-success btn-sm" @click="aniadir($event.target)">
                                        +
                                    </button>
                                </div>
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
                                <div class="centrar">
                                    <button type="button" class="btn btn-danger btn-sm me-1" @click="quitar($event.target)">
                                        -
                                    </button>
                                    <span id="spanPocion" class="me-1">0</span>
                                    <button type="button" class="btn btn-success btn-sm" @click="aniadir($event.target)">
                                        +
                                    </button>
                                </div>
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
                                <div class="centrar">
                                    <button type="button" class="btn btn-danger btn-sm me-1" @click="quitar($event.target)">
                                        -
                                    </button>
                                    <span id="spanAntidoto" class="me-1">0</span>
                                    <button type="button" class="btn btn-success btn-sm" @click="aniadir($event.target)">
                                        +
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="modal-footer">
                <div class="row">
                    <div class="col-sm-12 text-end">
                        <button type="button" class="btn btn-secondary me-1" id="botonRegresarAlInventario" @click="cerrarTienda()">
                            Atras
                        </button>
                        <button type="button" class="btn btn-primary" @click="comprar()">
                            Comprar
                        </button>
                    </div>
                    <div class="col-sm-12 text-end">
                        <small class="text-warning" id="alerta" hidden>No se puede tener mas de 15 pokeballs y 5 pociones/antidotos.</small>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data(){
            return {
                POKEBALLMAX:15,
                POCIONESMAX:5,
                MINIMO:0,
                sumaBallsInventario:0,
                sumaPocionesInventario:0
            }
        },
        methods: {
            cerrarTienda()
            {
                let alerta=document.getElementById('alerta');
                alerta.setAttribute('hidden','true');
                this.$emit('cerrar-tienda');
            },
            aniadir(botonAniadir)
            {
                let span=botonAniadir.previousElementSibling;
                let cantidad=Number(span.textContent);
                if(span.id==="spanPocion"||span.id==="spanAntidoto")
                {
                    if(cantidad<this.POCIONESMAX)
                    {
                        span.textContent=String(cantidad+1);
                    }
                }
                else if(cantidad<this.POKEBALLMAX)
                {
                    span.textContent=String(cantidad+1);
                }
            },
            quitar(botonQuitar)
            {
                let span=botonQuitar.nextElementSibling;
                let cantidad=Number(span.textContent);
                if(cantidad>this.MINIMO)
                {
                    span.textContent=String(cantidad-1);
                }
            },
            comprar()
            {
                let alerta=document.getElementById('alerta');

                let duskBallInventario=Number(this.inventario.duskBall);
                let greatBallInventario=Number(this.inventario.greatBall);
                let healBallInventario=Number(this.inventario.healBall);
                let masterBallInventario=Number(this.inventario.masterBall);
                let repeatBallInventario=Number(this.inventario.repeatBall);
                let pocionInventario=Number(this.inventario.pocion);
                let antidotoInventario=Number(this.inventario.antidoto);
                this.sumaBallsInventario=duskBallInventario+greatBallInventario+healBallInventario+masterBallInventario+repeatBallInventario;
                this.sumaPocionesInventario=pocionInventario+antidotoInventario;

                let spanDuskBall=document.getElementById('spanDuskBall');
                let spanGreatBall=document.getElementById('spanGreatBall');
                let spanHealBall=document.getElementById('spanHealBall');
                let spanMasterBall=document.getElementById('spanMasterBall');
                let spanRepeatBall=document.getElementById('spanRepeatBall');
                let spanPocion=document.getElementById('spanPocion');
                let spanAntidoto=document.getElementById('spanAntidoto');

                let duskBall=Number(spanDuskBall.textContent);
                let greatBall=Number(spanGreatBall.textContent);
                let healBall=Number(spanHealBall.textContent);
                let masterBall=Number(spanMasterBall.textContent);
                let repeatBall=Number(spanRepeatBall.textContent);
                let pocion=Number(spanPocion.textContent);
                let antidoto=Number(spanAntidoto.textContent);

                spanDuskBall.textContent="0";
                spanGreatBall.textContent="0";
                spanHealBall.textContent="0";
                spanMasterBall.textContent="0";
                spanRepeatBall.textContent="0";
                spanPocion.textContent="0";
                spanAntidoto.textContent="0";

                let sumaBallsTienda=duskBall+greatBall+healBall+masterBall+repeatBall;
                let sumaPocionesTienda=pocion+antidoto;
                if(Number(sumaBallsTienda)+Number(this.sumaBallsInventario)>Number(this.POKEBALLMAX)||Number(sumaPocionesTienda)+Number(this.sumaPocionesInventario)>Number(this.POCIONESMAX))
                {
                    alerta.removeAttribute('hidden');
                }
                else
                {
                    let inventarioActualizado=
                    {
                        'duskBall':`${duskBall+duskBallInventario}`,
                        'greatBall':`${greatBall+greatBallInventario}`,
                        'healBall':`${healBall+healBallInventario}`,
                        'masterBall':`${masterBall+masterBallInventario}`,
                        'repeatBall':`${repeatBall+repeatBallInventario}`,
                        'pocion':`${pocion+pocionInventario}`,
                        'antidoto':`${antidoto+antidotoInventario}`
                    };

                    this.$emit('actualizar-inventario',inventarioActualizado);

                    alerta.setAttribute('hidden','true');

                    let datos=
                    {
                        inventario:
                        {
                            duskBall:inventarioActualizado.duskBall,
                            greatBall:inventarioActualizado.greatBall,
                            healBall:inventarioActualizado.healBall,
                            masterBall:inventarioActualizado.masterBall,
                            repeatBall:inventarioActualizado.masterBall,
                            pocion:inventarioActualizado.pocion,
                            antidoto:inventarioActualizado.antidoto
                        }
                    }
                    let datosJSON=JSON.stringify(datos);

                    localStorage.setItem('datosInventario',datosJSON);

                    this.cerrarTienda();
                }
            }
        },
        props: {
            inventario: Object
        },
        created(){
        },
    }
</script>

<style>
    .centrar
    {
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>