<template>
    <div class="list-container">
        <a :href="'/productos/' + instrumento.id">
            <b-card :img-src="'/img/' + instrumento.imagen" 
            img-alt="Card image" 
            img-left class="mb-3"
            style="object-fit: none; padding: 20px !important;">
            <p class="instrumento">
                {{ instrumento.instrumento }}
            </p>
            <p class="precio">
                $ {{ instrumento.precio }}
            </p>
            <b-card-text>
                <div v-if="instrumento.costoEnvio == 'G'" class="costo-envio">
                    <b-img src="/img/camion.png" img-alt="Instrumento image card" class="icon-camion"></b-img>
                    <b-card-text class="envio-verde">Envío gratis a todo el país</b-card-text>
                </div>
                <div v-else>
                    <b-card-text class="envio-naranja">
                        Costo de Envío Interior de Argentina: ${{instrumento.costoEnvio}}
                    </b-card-text>
                </div>
            </b-card-text>
            <b-card-text>
                {{ instrumento.cantidadVendida }} vendidos
            </b-card-text>
            </b-card>
        </a>
    </div>
</template>

<script>
export default {
    props: ["instrumento"]
};
</script>

<style scoped>
    .list-container {
        width: 50rem;
        align-self: center;
        text-align: left;
    }
    a {
        color: unset;
        text-decoration-line: none;
    }
    .instrumento {
        font-size: large;
    }
    .precio {
        font-size: xx-large;
        font-weight: bold;
    }
    .costo-envio{
        display: flex;
        flex-direction: row;
    }
    .envio-verde{
        color: green;
    }
    .envio-naranja{
        color: orange;
    }
</style>