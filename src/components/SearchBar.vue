<template>
    <div>
        <h1>{{headline}}</h1>
        <v-row>
            <v-col>
                <v-text-field
                        v-model="input"
                >
                </v-text-field>
            </v-col>
            <v-col>
                <v-btn @click="$emit('search', input)">Search</v-btn>
            </v-col>
        </v-row>
    </div>
</template>

<script>
    export default {
        name: "SearchBar",
        props: ["headline"],
        data: () => {
            return {
                input: ""
            }
        }
    }
</script>

<style scoped>

</style>
