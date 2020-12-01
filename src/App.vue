<template>
<div id="app">
    <b-navbar toggleable="lg" type="light">
        <b-navbar-brand href="#">MissWorldService</b-navbar-brand>

        <b-navbar-nav class="ml-auto">
            <b-nav-item href="#">Link</b-nav-item>
            <b-nav-item href="#">Disabled</b-nav-item>
        </b-navbar-nav>
    </b-navbar>

    <router-view @login="onLogin"/>
</div>
</template>

<script>
export default {
    name: 'App',
    components: {},
    data() {
        return {
            accessToken: ""
        }
    },
    mounted() {
        if (this.$route.path !== "/register" && !this.accessToken.trim()) {
            this.$router.push("/register");
        }
    },
    methods: {
        onLogin(tokens) {
            this.accessToken = tokens.accessToken;
            this.$router.push("/");
        }
    }
}
</script>

<style>
#app {
    width: 80%;
    margin: 0 auto;
}
</style>
