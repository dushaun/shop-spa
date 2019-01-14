<template>
    <b-navbar toggleable="md" fixed variant="light" class="py-4">
        <b-container>
            <b-navbar-toggle target="navbarNav"></b-navbar-toggle>
            <b-navbar-brand class="navbar-brand" :to="{ name: 'index' }">Navbar</b-navbar-brand>
            <b-collapse is-nav id="navbarNav">
                <b-navbar-nav class="navbar-nav mr-auto">
                    <template v-for="category in categories">
                        <template v-if="category.children.length">
                            <b-nav-item-dropdown
                                :text="category.name"
                                :key="category.slug"
                            >
                                <b-dropdown-item
                                    :to="{ name: 'categories-slug', params: { slug: category.slug }}"
                                >
                                    {{ category.name }}
                                </b-dropdown-item>
                                <b-dropdown-divider></b-dropdown-divider>
                                <b-dropdown-item
                                    v-for="child in category.children"
                                    :to="{ name: 'categories-slug', params: { slug: child.slug }}"
                                    :key="child.slug"
                                >
                                    {{ child.name }}
                                </b-dropdown-item>
                            </b-nav-item-dropdown>
                        </template>

                        <template v-else>
                            <b-nav-item
                                :to="{ name: 'categories-slug', params: { slug: category.slug }}"
                                :key="category.slug"
                            >
                                {{ category.name }}
                            </b-nav-item>
                        </template>
                    </template>
                </b-navbar-nav>
                <b-navbar-nav class="ml-auto">
                    <template v-if="!$auth.loggedIn">
                        <b-nav-item :to="{ name: 'auth-signin' }">
                            Sign in
                        </b-nav-item>
                    </template>

                    <template v-else>
                        <b-nav-item href="#">
                            {{ $auth.user.name }}
                        </b-nav-item>
                        <b-nav-item href="#">
                            Orders
                        </b-nav-item>
                        <b-nav-item :to="{ name: 'cart' }">
                            Cart ({{ cartCount }})
                        </b-nav-item>
                    </template>
                </b-navbar-nav>
            </b-collapse>
        </b-container>
    </b-navbar>
</template>

<script>
    import { mapGetters } from 'vuex'

    export default {
        computed: {
            ...mapGetters({
                categories: 'categories',
                cartCount: 'cart/count'
            })
        }
    }
</script>