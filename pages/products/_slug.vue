<template>
    <b-container>
        <b-row>
            <b-col>
                <b-img src="http://via.placeholder.com/620x620" />
            </b-col>
            <b-col>
                <b-card :title="product.name">
                    <p class="card-text"
                        v-if="product.description">
                        {{ product.description }}
                    </p>
                    <hr>
                    <b-badge variant="secondary">
                        {{ product.price }}
                    </b-badge>
                    <hr>
                    <b-form>
                        <ProductVariation
                            v-for="(variations, type) in product.variations"
                            :type="type"
                            :variations="variations"
                            :key="type"
                        />
                    </b-form>
                </b-card>
            </b-col>
        </b-row>
    </b-container>
</template>

<script>
    import ProductVariation from '@/components/products/ProductVariation'

    export default {
        data () {
            return {
                product: null
            }
        },

        components: {
            ProductVariation
        },

        async asyncData ({ params, app }) {
            let response = await app.$axios.$get(`products/${params.slug}`)

            return {
                product: response.data
            }
        }
    }
</script>