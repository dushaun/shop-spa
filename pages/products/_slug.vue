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
                        Product price
                    </b-badge>
                </b-card>
            </b-col>
        </b-row>
    </b-container>
</template>

<script>
    export default {
        data () {
            return {
                product: null
            }
        },
        // mounted () {
        //     this.$nextTick(() => {
        //         this.$nuxt.$loading.start()
        //
        //         setTimeout(() => this.$nuxt.$loading.finish(), 500)
        //     })
        // },
        async asyncData ({ params, app }) {
            let response = await app.$axios.$get(`products/${params.slug}`)

            return {
                product: response.data
            }
        }
    }
</script>