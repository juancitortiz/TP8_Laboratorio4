<template>
    <div class="container">
        <div class="left-side">
            <img :src="'/img/' + instrumentoEncontrado.imagen" 
            img-alt="Card image"
            class="instr-img">
            <div style="text-align: left;">
                <p>Descripción:</p>
                <b-card-text class="descripcion">
                {{ instrumentoEncontrado.descripcion }}
                </b-card-text>
            </div>
            
        </div>
        <b-card style="max-width: 20rem; text-align: left;">
            <b-card-text class="vendidos">
                {{ instrumentoEncontrado.cantidadVendida }} vendidos
            </b-card-text>
            <b-card-text class="instrumento">
                {{ instrumentoEncontrado.instrumento }}
            </b-card-text>
            <b-card-text  class="precio">
                $ {{ instrumentoEncontrado.precio }}
            </b-card-text>
            <div class="marc-mod">
                <p>Marca: {{ instrumentoEncontrado.marca }}</p>
                <p>Modelo: {{ instrumentoEncontrado.modelo }}</p>
            </div>
            <b-card-text>
                Costo envío:
                <div v-if="instrumentoEncontrado.costoEnvio == 'G'" class="costo-envio">
                    <b-img src="/img/camion.png" img-alt="Instrumento image card" class="icon-camion"></b-img>
                    <b-card-text class="envio-verde">Envío gratis</b-card-text>
                </div>
                <div v-else>
                    <b-card-text class="envio-naranja">
                        Costo de Envío: ${{instrumentoEncontrado.costoEnvio}}
                    </b-card-text>
                </div>
            </b-card-text>
            <b-button href="#" variant="outline-primary">Agregar a carrito</b-button>
        </b-card>
    </div>
</template>

<script>
export default {
  name: "DetalleInstrumento",
  components: {},
  mounted() {
    this.getInstrumentoId();
  },
  data() {
    return {
      instrumentoEncontrado: []
    };
  },
  methods: {
    async getInstrumentoId() {
      const parametroId = this.$route.params.id;
      const res = await fetch("/instrumentos.json");
      const resJson = await res.json();
      console.log(resJson);
      this.instrumentoEncontrado = await resJson.instrumentos.find(
        instrum => instrum.id === parametroId
      );
      console.log(this.instrumentoEncontrado);
    }
  }
};
</script>

<style scoped>
    .container {
        width: 60rem;
        max-height: 85vh;
        display: flex;
        flex-direction: row;
    }
    .left-side {
        display: flex;
        flex-direction: column;
    }
    .instr-img {
        object-fit: none;
        min-width: 20rem;
        padding: 5px;
    }
    .descripcion {
        font-size: small;
    }
    a {
        color: unset;
        text-decoration-line: none;
    }
    .vendidos {
        font-size: small;
    }
    .instrumento {
        font-size: x-large;
        font-weight: bold;
    }
    .precio {
        font-size: xx-large;
    }
    .marc-mod {
        font-size: small;
        margin-bottom: 1rem;
    }
    .marc-mod > p {
        margin-bottom: 0;
        font-weight: bold;
    }
    .costo-envio{
        display: flex;
        flex-direction: row;
        margin-bottom: 7rem;
    }
    .envio-verde{
        color: green;
    }
    .envio-naranja{
        color: orange;
    }
</style>