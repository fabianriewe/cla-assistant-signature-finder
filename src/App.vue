<template>
  <v-app>
    <v-content>
        <h1>By Repo:</h1>
        <v-text-field
                v-model="repoId"
        >
        </v-text-field>
        <v-btn @click="usersBySignature()">Search</v-btn>
        <div v-if="loading">
            <v-progress-circular
                    indeterminate
                    color="primary"
            ></v-progress-circular>
        </div>
        <div v-else>
            <user :user="user"  v-for="(user, index) in users " :key="index"></user>
        </div>
    </v-content>
  </v-app>
</template>

<script>
import User from './components/User';

export default {
  name: 'App',

  components: {
    User,
  },

  data: () => ({
    users: [],
      repoId: undefined,
      loading: false
  }),
  methods: {
    async usersBySignature() {
        if (this.repoId) {
            this.loading = true;
            const response = await this.axios.get('/repos?repo_id=' + this.repoId);
            this.users = response.data;
            this.loading = false;
        }
    }
  },
  async mounted() {
  }
};
</script>
