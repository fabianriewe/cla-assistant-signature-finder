<template>
    <v-card>
        <v-card-title>{{signature[0]}} ({{ signature[1]}})</v-card-title>
        <v-card-subtitle>Pull request: {{signature[4]}}</v-card-subtitle>
        <v-card-text>
            <div>Date: {{ new Date(parseInt(signature[5])).toLocaleDateString("de-DE")}}</div>
        </v-card-text>
    </v-card>
</template>

<script>
    export default {
        name: "User",
        props: ["signature"]
    }
</script>

<style scoped>

</style>
