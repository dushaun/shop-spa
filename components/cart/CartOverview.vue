<template>
    <!--<b-table striped hover></b-table>-->

    <table class="table table-borderless table-hover">
        <tbody>
            <CartOverviewProduct
                v-for="product in products"
                :key="product.id"
                :product="product"
            />
        </tbody>
    </table>

    <!--<b-card title="Card Title"-->
            <!--class="mb-4">-->
        <!--<p class="card-text">-->
            <!--Some quick example text to build on the card title and make up the bulk of the card's content.-->
        <!--</p>-->
        <!--<b-button href="#" variant="primary">Something</b-button>-->
    <!--</b-card>-->
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