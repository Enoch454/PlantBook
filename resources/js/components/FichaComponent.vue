<template>
    <div>
        <h3>{{nombre}}</h3>
        <p>{{nCientifico}}</p>
        <p>{{nAlterno}}</p>
        <p>{{info}}</p>
        <p>{{pathImagen}}</p>
        <p>{{imagen}}</p>
        <img v-bind:src="imagen" alt="una flor">
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
        data(){
            return {
                imagen: "http://localhost/storage/"+this.pathImagen,
            }
        }
    }
</script>

<style>

</style>