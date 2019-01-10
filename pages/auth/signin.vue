<template>
    <b-container>
        <b-row class="justify-content-md-center">
            <b-col cols="4">
                <h4>Sign in</h4>
                <br>
                <b-form @submit.prevent="signin">
                    <b-form-group id="emailSigninGroup"
                        label="Email"
                        label-for="emailSignin"
                        description="We'll never share your email with anyone else."
                    >
                        <b-form-input id="emailSignin"
                            type="email"
                            required
                            placeholder="e.g. you@somewhere.com"
                            v-model="form.email"
                        >
                        </b-form-input>
                    </b-form-group>
                    <b-form-group id="passwordSigninGroup"
                        label="Password"
                        label-for="passwordSignin"
                    >
                        <b-form-input id="passwordSignin"
                            type="password"
                            required
                            v-model="form.password"
                        >
                        </b-form-input>
                    </b-form-group>
                    <b-button class="btn-block"
                        type="submit"
                        variant="primary"
                    >
                        Sign in
                    </b-button>
                </b-form>
            </b-col>
        </b-row>
    </b-container>
</template>

<script>
    export default {
        data () {
            return {
                form: {
                    email: '',
                    password: ''
                }
            }
        },

        methods: {
            async signin () {
                await this.$auth.loginWith('local', {
                    data: this.form
                })

                this.$router.replace({
                    name: 'index'
                })
            }
        }
    }
</script>