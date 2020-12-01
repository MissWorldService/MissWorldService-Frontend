<template>
<main>
    <h1>Please, login or register!</h1>
    <b-form @submit.prevent="onSubmit">

        <b-form-group
            id="input-group-1"
        >
            <label for="input-1">Username:</label>
            <input
                type="text"
                class="form-control"
                id="input-1"
                v-model="form.username"
                placeholder="Enter Username"
                required
            >
        </b-form-group>

        <b-form-group
            id="input-group-2"
        >
            <label for="input-2">Password:</label>
            <input
                type="password"
                class="form-control"
                id="input-2"
                v-model="form.password"
                placeholder="Enter Password"
                required
            >
        </b-form-group>

        <b-button class="btn" type="submit" variant="primary" @click="type = 'login'">Log-in
        </b-button>
        <b-button class="btn" type="submit" variant="secondary" @click="type = 'register'">
            Register
        </b-button>
    </b-form>
</main>
</template>

<script>
import settings from "@/settings";

export default {
    name: "Register",
    data() {
        return {
            form: {
                username: "",
                password: ""
            },
            type: ""
        }
    },
    methods: {
        async onSubmit() {
            const res = await fetch(settings.hostname + this.type, {
                method: "POST",
                body: JSON.stringify(this.form)
            });
            this.$emit('login', await res.json())
        }
    }
}
</script>

<style scoped>
main {
    width: 60%;
    margin: 0 auto;
}

h1 {
    text-align: center;
    margin: 10px 0;
}

.btn {
    margin: 0 10px 0 0;
}
</style>
