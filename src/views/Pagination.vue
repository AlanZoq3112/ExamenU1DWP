<template>
    <div class="overflow-auto">
        <b-table id="my-table" :items="items" :per-page="perPage" :current-page="currentPage" small></b-table>

        <b-row>
            <b-col>
                <p class="mt-3">Current Page: {{ currentPage }}</p>
            </b-col>
            <b-col>
                <b-pagination v-model="currentPage" :total-rows="rows" :per-page="perPage" aria-controls="my-table"></b-pagination>
            </b-col>
            
        </b-row>



    </div>
</template>

<script>
export default {
    name: "pagination",
    data() {
        return {
            perPage: 3,
            currentPage: 1,
            items: [
                { Marca: 'Nissan', Modelo: 'Sentra', Año: '2020', NoSerie: 'ABCD123-45AB ' },
                { Marca: 'Nissan', Modelo: 'Sentra', Año: '2021', NoSerie: 'ABCD123-45AB ' },
                { Marca: 'Nissan', Modelo: 'Sentra', Año: '2022', NoSerie: 'ABCD123-45AB ' },
                { Marca: 'Nissan', Modelo: 'Sentra', Año: '2023', NoSerie: 'ABCD123-45AB ' },
                { Marca: 'Nissan', Modelo: 'Sentra', Año: '2024', NoSerie: 'ABCD123-45AB ' },
                { Marca: 'Nissan', Modelo: 'Skiline', Año: '1999', NoSerie: 'ABCD123-45AB ' },
                { Marca: 'Nissan', Modelo: 'GTR Skiline', Año: '2020', NoSerie: 'ABCD123-45AB ' },
                { Marca: 'Nissan', Modelo: 'GTR Skiline NISMO', Año: '2020', NoSerie: 'ABCD123-45AB ' },
                { Marca: 'Toyota', Modelo: 'Supra', Año: '1998', NoSerie: 'ABCD123-45AB ' },
            ]
        }
    },
    computed: {
        rows() {
            return this.items.length
        }
    }
}
</script>

<style scoped></style>