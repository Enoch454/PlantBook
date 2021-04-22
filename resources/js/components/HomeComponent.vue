<template>
    <div class="">

        

        <div class="card">
            <div class="card-body">
                <div v-for="planta in lista_plantas" :key="planta.id">
                    <button class="ripple" @click="seleccionar(planta.id)">
                        <img
                            alt="una flor"
                            class="img-fluid rounded"
                            v-bind:src="get_pathImagen(planta.pathImagen)"
                        />
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data () {
            return{
                lista_plantas: [],
                planta_seleccionada: -1,
            }
        },
        methods: {
            async listar() {
                const res = await axios.get('/plantas');
                this.lista_plantas = res.data;
            },
            get_pathImagen(path_imagen){
                var path = "http://localhost/storage/"+path_imagen;
                console.log(path)
                return path;
            },
            seleccionar(id){
                this.planta_seleccionada = id;
                console.log(this.planta_seleccionada);
            }
        },
        created() {
            //console.log('Component mounted.')
            this.listar();
        },
        mounted() {
                console.log(this.lista_plantas)
        },
    }
</script>
