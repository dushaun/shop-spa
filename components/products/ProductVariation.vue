<template>
    <div>
        <!--<p>{{ type }}</p>-->
        <b-form-group :id="type + SelectGroup"
              :label="type"
              :label-for="type + SelectField"
        >
            <b-form-select :id="type + SelectField"
                    v-model="selected"
                    size="sm"
            >
                <option :value="null">Please select an option</option>
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
            }
        },

        data () {
            return {
                selected: null
            }
        }
    }
</script>