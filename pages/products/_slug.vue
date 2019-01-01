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
                            v-model="form.variation"
                        />

                        <b-row v-if="form.variation">
                            <b-col cols="6">
                                <b-input-group>
                                    <b-form-select size="sm"
                                        :value="quantity.selected">
                                        <option value="">1</option>
                                    </b-form-select>

                                    <b-input-group-append>
                                        <b-btn variant="secondary" size="sm">Add to Cart</b-btn>
                                    </b-input-group-append>
                                </b-input-group>
                            </b-col>
                        </b-row>
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
                product: null,
                form: {
                    variation: null,
                    quantity: 1
                },
                quantity: {
                    selected: ''
                }
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