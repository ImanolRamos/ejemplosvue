<template>
  <div id="app">
    <mostrar-tabla :iva="IVA"></mostrar-tabla>
    <input type="text" v-model="search"/>
    <table id="example-1">
      <th>Referencia</th><th>Precio Unitario</th><th>Descuento pre-IVA</th><th>IVA</th><th>Precio Con IVA</th><th>Precio Sin IVA</th>
      <tr v-for="item in filteredItems">
        <td>{{ item.referencia }}</td>
        <td>{{ item.precio_unitario }}</td>
        <td>{{ item.descuento }}</td>
        <td>{{ IVA*100 }}%</td>
        <td>{{ calcularFinal(item.precio_unitario, item.descuento) }}</td>
        <td>{{ item.precio_sin_iva}}</td>
      </tr>
    </table>
  </div>
</template>

<script>
import MostrarTabla from './components/mostrarTabla.vue'

export default {
  name: 'App',
  components: {
    MostrarTabla
  },

  data() {
    return {
      search: "",
      items: [
        { referencia: 'AAE', precio_unitario: 40, descuento: 7 },
        { referencia: 'ABC', precio_unitario: 21, descuento: 3 },
        { referencia: 'DEF', precio_unitario: 89, descuento: 4 },
        { referencia: 'AEF', precio_unitario: 38, descuento: 5 }
      ],
      IVA: 0.107
    }
  },

  computed: {
    precio_final(){
      return (this.items.precio_unitario-this.items.descuento)*this.IVA+(this.items.precio_unitario-this.items.descuento)
    },

    filteredItems(){
      return this.items.filter((item) => item.referencia.toLowerCase().includes(this.search.toLowerCase()))
    }
  },

  methods: {
    calcularFinal(p_u, desc){
      return (p_u-desc)*this.IVA+(p_u-desc)
    },
  },

  created() {
    this.items.map((item) => item['precio_sin_iva'] = item.precio_unitario-item.descuento);
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
