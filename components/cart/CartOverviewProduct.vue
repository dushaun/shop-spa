<template>
    <tr>
        <td width="120">
            <img src="http://via.placeholder.com/60x60" alt="">
        </td>
        <td>
            {{ product.product.name }} - {{ product.name }}
        </td>
        <td width="160">
            <select class="custom-select">
                <option value="0">0</option>
                <option
                    :value="x"
                    v-for="x in product.stock_count"
                    :key="x"
                    :selected="x === product.quantity"
                >
                    {{ x }}
                </option>
            </select>
        </td>
        <td>
            {{ product.total }}
        </td>
        <td>
            <a href="" @click.prevent="destroyProduct(product.id)">remove</a>
        </td>
    </tr>
</template>

<script>
    import { mapActions } from 'vuex'

    export default {
        props: {
            product: {
                required: true,
                type: Object
            }
        },

        methods: {
            ...mapActions({
                destroy: 'cart/destroy'
            }),

            destroyProduct (productId) {
                if (confirm('Are you sure?')) {
                    this.destroy(productId)
                }
            }
        }
    }
</script>