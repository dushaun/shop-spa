<template>
    <b-navbar toggleable="md" fixed variant="light">
        <b-container>
            <b-navbar-toggle target="navbarNav"></b-navbar-toggle>
            <b-navbar-brand class="navbar-brand" :to="{ name: 'index' }">Navbar</b-navbar-brand>
            <b-collapse is-nav id="navbarNav">
                <b-navbar-nav class="navbar-nav mr-auto">
                    <template v-for="category in categories">
                        <template v-if="category.children.data.length">
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
                                    v-for="child in category.children.data"
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
                    <b-nav-item>Sign in</b-nav-item>
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
                categories: 'categories'
            })
        }
    }
</script>