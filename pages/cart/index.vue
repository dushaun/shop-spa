<template>
    <b-container>
        <b-row class="justify-content-md-center">
            <b-col cols="9">
                <b-card title="Your Cart">
                    <br>
                    <CartOverview/>
                    <b-form>
                        <b-button class="btn-block"
                                  type="submit"
                                  variant="primary"
                        >
                            Checkout
                        </b-button>
                    </b-form>
                </b-card>
            </b-col>
        </b-row>
    </b-container>
</template>

<script>
    import CartOverview from '@/components/cart/CartOverview'

    export default {
        components: {
            CartOverview
        }
    }
</script>