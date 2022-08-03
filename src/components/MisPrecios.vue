<template>
    <div>
        PU:<input v-model="nuevo_precio_unitario"/>
        CANTIDAD:<input v-model="nueva_cantidad"/>
        <button @click="calcular">
            Calcular
        </button>
        <button @click="cancelar">
            Cancelar
        </button>
        </br>
        Resultado:<span>{{cresultado}}</span>
        <br>
        <button @click="guardar">Guardar</button>
    </div>
</template>
<script>


export default {

    props:{
        'cantidad':Number,
        'precio_unitario':Number,
    },//fin de los props


    data() {
        return {
            nueva_cantidad:null,
            nuevo_precio_unitario:null,
            // resultado:null,
            nuevosValores:{
                'cantidad':null,
                'precio_unitario':null
            }
        }
    },// fin de data


    computed: {
        cresultado(){
            return this.nuevosValores.cantidad*this.nuevosValores.precio_unitario;
        }
    },// fin de las computadas

    methods: {
        calcular(){
            // this.resultado = this.nueva_cantidad*this.nuevo_precio_unitario;
            this.nuevosValores.cantidad=this.nueva_cantidad;
            this.nuevosValores.precio_unitario=this.nuevo_precio_unitario;
        },
        cancelar(){
            this.nueva_cantidad=this.cantidad;
            this.nuevo_precio_unitario=this.precio_unitario;
        },

        guardar(){
            this.$emit('guardar', this.nuevosValores);
        }
    },


    created() {
        this.nueva_cantidad=this.cantidad;
        this.nuevo_precio_unitario=this.precio_unitario;
    },//fin del created

    
}
</script>
<style>
    
</style>