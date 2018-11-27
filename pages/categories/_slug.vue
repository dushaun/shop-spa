<template>
    <b-container>
        <b-row class="col-4" v-for="product in products" :key="product.slug">
            <Product :product="product" />
        </b-row>
    </b-container>
</template>

<script>
    import Product from '@/components/products/Product'

    export default {
        data () {
            return {
                products: []
            }
        },

        components: {
            Product
        },

        async asyncData ({ params, app }) {
            let response = await app.$axios.$get(`products?category=${params.slug}`)

            return {
                products: response.data
            }
        }
    }
</script>