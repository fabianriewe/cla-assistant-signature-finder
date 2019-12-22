<template>
      <div>
        <v-row>
          <v-col>
            <v-icon>mdi-github-circle</v-icon>{{signature[0]}} ({{ signature[1]}})
          </v-col>
          <v-col>
            <v-icon>mdi-source-pull</v-icon>{{signature[4]}}
            <v-icon>mdi-comment-outline</v-icon>{{signature[2]}}
            <v-icon>mdi-calendar-range</v-icon>{{ new Date(parseInt(signature[5])).toLocaleDateString("de-DE") }}
          </v-col>
        </v-row>
      </div>
</template>

<script>
    export default {
        name: "User",
        props: ["signature"]
    }
</script>

<style scoped>

</style>
