<template>
    <div class="">

        <!-- Modal -->
        <div class="modal" :class="{mostrar : modalActivo}" style="overflow-y: scroll">
            <div class="modal-dialog" style="width:1250px;">
                <div class="modal-content">
                    <div class="modal-header">
                        <div>
                            <h4 class="modal-title">{{planta_seleccionada.nombre}}</h4>
                            <h6 class="modal-title">{{planta_seleccionada.nCientifico}}</h6>
                        </div>
                        <button type="button" class="close" data-dismiss="modal" aria-label="Close" @click="cerrarModal();">
                        <span aria-hidden="true">&times;</span>
                        </button>
                    </div>
                    <div class="modal-body">
                        <!--
                        <div>
                            <div class="ripple">
                                <img
                                    alt="una flor"
                                    class="img-fluid rounded"
                                    v-bind:src="get_pathImagen(planta_seleccionada.plantaImagen)"
                                />
                            </div>
                        </div>
                        <div>
                            <p>{{planta_seleccionada.info}}</p>
                        </div>
                        <div>
                            <p>Tambien conocido como</p>
                            <p>{{planta_seleccionada.nAlterno}}</p>
                        </div>
                        -->

                        <div class="container-fluid">
                            <div class="row">
                                <div class="col-md-4">
                                    <img
                                        alt="una flor"
                                        class="img-fluid rounded"
                                        v-bind:src="get_pathImagen(planta_seleccionada.plantaImagen)"
                                    />
                                </div>
                                <div class="col-md-8">
                                    <p>{{planta_seleccionada.info}}</p>
                                    <p>Tambien conocido como</p>
                                    <p>{{planta_seleccionada.nAlterno}}</p>
                                </div>
                            </div>
                        </div>

                    </div>
                </div>
            </div>
        </div>




        <div class="card">
            <div class="card-body">
                <div v-for="planta in lista_plantas" :key="planta.id">
                    <button class="ripple" @click="seleccionar(planta)">
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
                planta_seleccionada: {
                    info:"",
                    nAlterno:"",
                    nCientifico:"",
                    nombre:"",
                    pathImagen:"",
                },
                modalActivo: false,

            }
        },
        methods: {
            async listar() {
                const res = await axios.get('/plantas');
                this.lista_plantas = res.data;
                console.log(this.lista_plantas);
            },
            get_pathImagen(path_imagen){
                var path = "http://localhost/storage/"+path_imagen;
                console.log(path)
                return path;
            },
            seleccionar(planta){
                this.planta_seleccionada.info = planta.info;
                this.planta_seleccionada.nAlterno = planta.nAlterno;
                this.planta_seleccionada.nCientifico = planta.nCientifico;
                this.planta_seleccionada.nombre = planta.nombre;
                this.planta_seleccionada.plantaImagen = planta.pathImagen;

                this.modalActivo=true;
                console.log(this.planta_seleccionada);
            },
            cerrarModal(){
                this.modalActivo=false;
            },
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

<style>
    .mostrar{
        display: list-item;
        opacity: 1;
        background: rgba(43, 43, 43, 0.705);
    }
    
   
    /*
    Full screen Modal 
    */
    .fullscreen-modal .modal-dialog {
    margin: 0;
    margin-right: auto;
    margin-left: auto;
    width: 100%;
    }
    @media (min-width: 768px) {
    .fullscreen-modal .modal-dialog {
        width: 750px;
    }
    }
    @media (min-width: 992px) {
    .fullscreen-modal .modal-dialog {
        width: 970px;
    }
    }
    @media (min-width: 1200px) {
    .fullscreen-modal .modal-dialog {
        width: 1170px;
    }
    }
</style>