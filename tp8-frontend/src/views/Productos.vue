<template>
    <div class="list">
        <div 
        v-for="instru in instrumentosData" :key="instru.id"
        >
            <instrumento :instrumento="instru"></instrumento>
        </div>
    </div>
</template>


<script>
import Instrumento from '@/components/Instrumento.vue';

export default {
    name: 'Productos',
    components: {
        'instrumento': Instrumento
    },
  mounted() {
    this.getInstrumentos();
  },
  data() {
    return {
      instrumentosData: []
    };
  },
  methods: {
    async getInstrumentos() {
      const res = await fetch("/instrumentos.json");
      const resJson = await res.json();
      console.log(resJson);
      this.instrumentosData = resJson.instrumentos;
    }
  }
}
</script>

<style scoped>
    .list {
        margin-left: 18rem;
    }
</style>