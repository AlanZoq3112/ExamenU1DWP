<template>
    <div>
        <br>
        <b-row>
            <b-col></b-col>
            <b-col cols="10">
                <b-card title="Registra un vehiculo" style="max-width 800px;" size="lg" class="mb-2">

                    <b-row>
                        <b-col>
                            <label for="">Marca</label>
                            <b-form-input type="text" :state="validarMarca" required placeholder="Ingresa la marca del auto"
                                v-model="form.brand"></b-form-input>
                            <b-form-invalid-feedback :state="validarMarca">
                                No se aceptan signos especiales
                            </b-form-invalid-feedback>
                            <b-form-valid-feedback :state="validarMarca">
                                Ta bien.
                            </b-form-valid-feedback>
                        </b-col>
                        <b-col>
                            <label for="">Modelo</label>
                            <b-form-input :state="validarModel" type="text" required placeholder="Modelo"
                                v-model="form.model"></b-form-input>
                            <b-form-invalid-feedback :state="validarModel">
                                No se aceptan signos especiales
                            </b-form-invalid-feedback>
                            <b-form-valid-feedback :state="validarModel">
                                Ta bien.
                            </b-form-valid-feedback>
                        </b-col>
                    </b-row>
                    <b-row>
                        <b-col>
                            <label for="">Año de fabricación</label>
                            <b-form-datepicker v-model="form.date" :min="minDate" :max="maxDate" required
                                placeholder="Seleccionar fecha"></b-form-datepicker>

                            <b-form-invalid-feedback :state="validarYear">
                                Año de fabricación no puede ser mayor al actual
                            </b-form-invalid-feedback>
                            <b-form-valid-feedback :state="validarYear">
                                Ta bien.
                            </b-form-valid-feedback>
                        </b-col>
                        <b-col>
                            <label for="">Numero de serie</label>
                            <b-form-input :state="validarSerie" type="text" required placeholder="XXXX000-00XX "
                                v-model="form.serie"></b-form-input>

                            <b-form-invalid-feedback :state="validarSerie">
                                X son letras y los 0 números: XXXX000-00XX
                            </b-form-invalid-feedback>
                            <b-form-valid-feedback :state="validarSerie">
                                Ta bien.
                            </b-form-valid-feedback>
                        </b-col>
                    </b-row>

                    <br>
                    <center><b-button variant="primary" type="submit" v-on:click="enviarForm">Enviar</b-button></center>



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
            const regex = /^[a-zA-Z0-9\s\-_.,]*$/;
            return this.form.brand.length > 0 && this.form.brand.length < 20 && regex.test(this.form.brand);
        },
        validarModel() {
            const regex = /^[a-zA-Z0-9\s\-_.,]*$/;
            return this.form.model.length > 0 && this.form.model.length < 20 && regex.test(this.form.model);
        },
        validarYear() {

            const currentYear = new Date().getFullYear();
            return this.form.year.length > 0 && this.form.year.length < 20 &&
                parseInt(this.form.year, 10) <= currentYear
        },
        validarSerie() {
            const regex = /^[A-Za-z]{4}\d{3}-\d{2}[A-Za-z]{2}$/;
            return this.form.serie.length > 0 && this.form.serie.length < 13 && regex.test(this.form.serie);
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