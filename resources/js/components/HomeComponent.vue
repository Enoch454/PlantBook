<template>
    <div class="col-md-10">
        <div class="card">
            <div class="card-body">
                <ficha-component
                    v-bind:nombre="this.lista_plantas[0].nombre"
                    v-bind:nCientifico="this.lista_plantas[0].nCientifico"
                    v-bind:nAlterno="this.lista_plantas[0].nAlterno"
                    v-bind:info="this.lista_plantas[0].info"
                    v-bind:pathImagen="this.lista_plantas[0].pathImagen"
                ></ficha-component>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data () {
            return{
                lista_plantas: [],
            }
        },
        methods: {
            async listar() {
                const res = await axios.get('/plantas');
                this.lista_plantas = res.data;
                console.log(this.lista_plantas)
            },
        },
        created() {
            //console.log('Component mounted.')
            this.listar();
        },
        mounted() {
            
        },
    }
</script>
