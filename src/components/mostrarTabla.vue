<template>
    <div>
        <div> prueba pasar datos hijo -> El iva general es: {{ iva * 100}}%</div>
    </div>
</template>
<script>
export default {
    name: 'mostrarTabla',
    props: {
        iva: Number,
        item: {
            ref: String,
            p_u: Number,
            desc: Number
            }
    }
}
</script>
<style>
    
</style>