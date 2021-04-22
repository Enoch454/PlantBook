<template>
    <div class="col-md-10">
        <div class="card">
            <div class="card-header">
                Example Component
            </div>
            <div class="card-body">
                <ficha-component
                    v-bind:nombre="lista_plantas[0].name"
                    v-bind:nCientifico="lista_plantas[0].nCientifico"
                    v-bind:nAlterno="lista_plantas[0].nAlterno"
                    v-bind:info="lista_plantas[0].info"
                    v-bind:pathImagen="lista_plantas[0].pathImagen"
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
