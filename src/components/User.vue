<template>
    <v-card>
        <v-card-title>{{user[0]}}</v-card-title>
        <v-card-subtitle>Pull request: {{user[4]}}</v-card-subtitle>
        <v-card-text>
            <div>Date: {{ new Date(parseInt(user[5])).toLocaleDateString("de-DE")}}</div>
        </v-card-text>
    </v-card>
</template>

<script>
    export default {
        name: "User",
        props: ["user"]
    }
</script>

<style scoped>

</style>
