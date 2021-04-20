<template>
    <div class="col-md-8">
        <div class="card">
            <div class="card-header">
                Example Component
            </div>
            <div class="card-body">
                I'm an example component.
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
            },
        },
        created() {
            this.listar();
        },
        mounted() {
            //console.log('Component mounted.')
            console.log(this.lista_plantas)
        },
    }
</script>
