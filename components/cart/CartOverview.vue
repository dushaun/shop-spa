<template>
    <table class="table table-borderless table-hover">
        <tbody>
            <CartOverviewProduct
                v-for="product in products"
                :key="product.id"
                :product="product"
            />
        </tbody>
    </table>
</template>

<script>
    import { mapGetters } from 'vuex'
    import CartOverviewProduct from '@/components/cart/CartOverviewProduct'

    export default {
        data () {
            return {
                table: {
                    fields: {

                    },
                    items: {

                    }
                }
            }
        },

        computed: {
            ...mapGetters({
                products: 'cart/products'
            })
        },

        components: {
            CartOverviewProduct
        }
    }
</script>