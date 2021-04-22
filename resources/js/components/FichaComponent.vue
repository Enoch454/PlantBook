<template>
    <div>
        <h3>Ficha Ejemplo</h3>
        <p>{{nombre}}</p>
        <p>{{nCientifico}}</p>
        <p>{{nAlterno}}</p>
        <p>{{info}}</p>
        <p>{{pathImagen}}</p>
    </div>
</template>

<script>
    export default {
        props: {
            nombre:String,
            nCientifico:String,
            nAlterno:String,
            info:String,
            pathImagen:String,
        },
    }
</script>

<style>

</style>