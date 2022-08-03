<template>
  <div id="app">
    <mis-precios 
      :cantidad="cantidad" 
      :precio_unitario="precio_unitario"
      @guardar="guardar"
      
    ></mis-precios>
  </div>
</template>

<script>
import MisPrecios from './components/MisPrecios.vue'
export default {
  name: 'App',
  components: {
    MisPrecios
  },
  

  data() {
    return {
      cantidad:0,
      precio_unitario:0,
    }
  },//fin de data

  methods: {
    guardar(payload){
      this.cantidad=parseFloat(payload.cantidad);
      this.precio_unitario=parseFloat(payload.precio_unitario);
    }
  },

}
</script>
