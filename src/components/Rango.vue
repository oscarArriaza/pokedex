<template>
    <div class="diplayFlex">
        <div class="me-1">
            <span id="spanRangoSlider1">
                1
            </span>
        </div>
        <div class="me-1">
            <div>
                <label for="rangoSlider" hidden>Slider 1</label>
                <input type="range" class="form-range slider" id="rangoSlider1" value="1" min="1" max="151" step="1" @click="enviarRango($event.target,$event.target.value)">
            </div>
            <div>
                <label for="rangoSlider" hidden>Slider 2</label>
                <input type="range" class="form-range slider" id="rangoSlider2" value="151" min="1" max="151" step="1" @click="enviarRango($event.target,$event.target.value)">
            </div>
        </div>
        <div>
            <span id="spanRangoSlider2">
                151
            </span>
        </div>
    </div>
</template>

<script>
    export default {
        data(){
            return {

            }
        },
        methods: {
            posicionarThumbs()
            {
                /*let rangoSlider1=document.getElementById('rangoSlider1');
                rangoSlider1.value=1;*/
            },
            /*enviarRango(slider,rango)
            {
                if(slider.id==="rangoSlider1")
                {
                    let spanRangoSlider1=document.getElementById('spanRangoSlider1');
                    spanRangoSlider1.innerHTML=rango;
                    let rangoDelOtroSlider=document.getElementById("rangoSlider2").value;
                    if(rango>=rangoDelOtroSlider)
                    {
                        rango=parseInt(rangoDelOtroSlider)-1;
                        slider.value=rango;
                    }
                    spanRangoSlider1.innerHTML=rango;
                    console.log(slider.value);
                }
                else
                {
                    let rangoDelOtroSlider=document.getElementById("rangoSlider1").value;
                    if(rango<=rangoDelOtroSlider)
                    {
                        rango=parseInt(rangoDelOtroSlider)+1;
                        slider.value=rango;
                    }
                    let spanRangoSlider2=document.getElementById('spanRangoSlider2');
                    spanRangoSlider2.innerHTML=rango;
                }
                //this.$emit('rango', rango)
                //console.log(rango)
            },*/
            enviarRango(slider, rango)
            {
                // Asegúrate de que el rango sea un número entero
                rango=parseInt(rango);

                if (slider.id==="rangoSlider1")
                {
                    let spanRangoSlider1 = document.getElementById('spanRangoSlider1');
                    let rangoDelOtroSlider = parseInt(document.getElementById("rangoSlider2").value);

                    // Asegúrate de que rango no sea mayor o igual al rango del otro slider
                    if (rango >= rangoDelOtroSlider)
                    {
                        rango = rangoDelOtroSlider - 1;
                    }

                    // Actualiza el slider y el span
                    slider.value = rango;
                    spanRangoSlider1.innerHTML = rango;
                }
                else
                {
                    let rangoDelOtroSlider = parseInt(document.getElementById("rangoSlider1").value);

                    // Asegúrate de que rango no sea menor o igual al rango del otro slider
                    if (rango <= rangoDelOtroSlider)
                    {
                        rango = rangoDelOtroSlider + 1;
                    }

                    // Actualiza el slider y el span
                    slider.value = rango;
                    let spanRangoSlider2 = document.getElementById('spanRangoSlider2');
                    spanRangoSlider2.innerHTML = rango;
                }

                //console.log(slider.value);
                // Si necesitas emitir el valor (dependiendo de tu framework), descomenta la siguiente línea:
                // this.$emit('rango', rango)
                let intervalo = [document.getElementById("rangoSlider1").value, document.getElementById("rangoSlider2").value];
                this.$emit('intervalo', intervalo); // Emisión del evento
            }

        },
        created(){
            this.posicionarThumbs()
        },
    }
</script>

<style>
    
    .slider-container
    {
        width: 300px;
        margin: 50px auto;
    }

    .slider
    {
        /*-webkit-appearance: none;*/
        width: 250px;
        height: 8px;
        /*background: #ddd;*/
        background:#E83283;
        outline: none;
        opacity: 0.7;
        transition: opacity .15s ease-in-out;
    }

    .slider:hover
    {
        opacity: 1;
    }

    .slider::-webkit-slider-thumb
    {
        -webkit-appearance: none;
        appearance: none;
        width: 20px;
        height: 20px;
        /*background: #007bff;*/
        background: white;
        cursor: pointer;
        border-radius: 50%;
    }

    .slider::-moz-range-thumb
    {
        width: 20px;
        height: 20px;
        /*background: #007bff;*/
        background: white;
        cursor: pointer;
        border-radius: 50%;
    }

    #valorSliderLabel
    {
        position: absolute;
        top: -25px; /* Ajustar el desplazamiento vertical */
        left: 50%; /* Centrar la etiqueta horizontalmente */
        transform: translateX(-50%); /* Mantener la posición centrada */
        font-size: 14px; /* Ajustar el tamaño de fuente según sea necesario */
        color: #ffecec; /* Establecer el color del texto */
    }

    .diplayFlex
    {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
</style>