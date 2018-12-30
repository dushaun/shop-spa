<template>
    <div>
        <b-form-group :id="type + 'SelectGroup'"
              :label="type"
              :label-for="type + 'SelectField'"
        >
            <b-form-select :value="selectedVariationId"
                    :id="type + 'SelectField'"
                    size="sm"
                    @change="changed($event, type)"
            >
                <option value="">Please select an option</option>
                <option v-for="variation in variations" :key="variation.id" :value="variation.id">
                    {{ variation.name }}
                    <template v-if="variation.price_varies">
                        ({{ variation.price }})
                    </template>
                </option>
            </b-form-select>
        </b-form-group>
    </div>
</template>

<script>
    export default {
        props: {
            type: {
                required: true,
                type: String
            },
            variations: {
                required: true,
                type: Array
            },
            value: {
                required: false,
                default: ''
            }
        },

        computed: {
            selectedVariationId () {
                if (!this.value) {
                    return ''
                }

                if (!this.findVariation(this.value.id)) {
                    return ''
                }

                return this.value.id
            }
        },

        methods: {
            changed (event, type) {
                this.$emit('input', this.findVariation(event))
            },

            findVariation (id) {
                let variation = this.variations.find(variation => variation.id === id)

                if (typeof variation === 'undefined') {
                    return null
                }

                return variation
            }
        }
    }
</script>