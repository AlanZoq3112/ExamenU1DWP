<template>
    <div>
        <br>
        <b-row>
            <b-col></b-col>
            <b-col cols="10">
                <b-card title="Registra un vehiculo" style="max-width 800px;" size="lg" class="mb-2">
                    <b-form>
                        <b-row>
                            <b-col>
                                <label for="">Marca</label>
                                <b-form-input type="text" :state="validarMarca" required
                                    placeholder="Ingresa la marca del auto" v-model="form.brand"></b-form-input>
                            </b-col>
                            <b-col>
                                <label for="">Modelo</label>
                                <b-form-input type="text" required placeholder="Modelo" v-model="form.model"></b-form-input>
                            </b-col>
                        </b-row>
                        <b-row>
                            <b-col>
                                <label for="">Año de fabricación</label>
                                <b-form-input type="number" required placeholder="Año de fabricación"
                                    v-model="form.year"></b-form-input>
                            </b-col>
                            <b-col>
                                <label for="">Numero de serie</label>
                                <b-form-input type="text" required placeholder="Numero de serie"
                                    v-model="form.serie"></b-form-input>
                            </b-col>
                        </b-row>

                        <br>
                        <center><b-button variant="primary" type="submit" v-on:click="enviarForm">Enviar</b-button></center>
                    </b-form>


                </b-card>
            </b-col>
            <b-col></b-col>
        </b-row>




    </div>
</template>

<script>
export default {
    name: "formulario",
    data() {
        return {
            form: {
                brand: "",
                model: "",
                serie: "",
                year: ""
            }
        }


    },
    computed: {
        validarMarca() {
            return this.form.brand.length > 0 && this.form.brand.length < 20
        }
    },
    methods: {
        enviarForm() {
            console.log("Se envia el formulario");
            console.log(this.form)
        }
    },
}
</script>

<style scoped></style>