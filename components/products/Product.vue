<template>
    <b-card no-body>
        <nuxt-link :to="link">
            <b-img rounded="top"
               fluid
               src="http://via.placeholder.com/1280x960" />
        </nuxt-link>
        <b-card-body>
            <h4 class="card-title">
                <nuxt-link :to="link">
                    {{ product.name }}
                </nuxt-link>
            </h4>
            <b-media>
                <p class="card-text" v-if="product.description">
                    {{ product.description }}
                </p>
            </b-media>
            <hr>
            <b-badge variant="secondary">
                {{ product.price }}
            </b-badge>
        </b-card-body>
    </b-card>
</template>

<script>
    export default {
        props: {
            product: {
                required: true,
                type: Object
            }
        },

        computed: {
            link () {
                return {
                    name: 'products-slug',
                    params: {
                        slug: this.product.slug
                    }
                }
            }
        }
    }
</script>