<template>
  <v-app>
    <v-content>
        <v-container>
          <v-row>
            <v-col><search-bar headline="By RepoId" @search="signaturesByRepo"></search-bar></v-col>
            <v-col><search-bar headline="By UserId" @search="signaturesByUser"></search-bar></v-col>
          </v-row>
          <div v-if="loading">
              <v-progress-circular
                      indeterminate
                      color="primary"
              ></v-progress-circular>
          </div>
          <div v-else>
              <user :user="user"  v-for="(user, index) in users " :key="index"></user>
          </div>
        </v-container>
    </v-content>
  </v-app>
</template>

<script>
import User from './components/User';
import SearchBar from './components/SearchBar';

export default {
  name: 'App',

  components: {
    User,
      SearchBar,
  },

  data: () => ({
    users: [],
      loading: false
  }),
  methods: {
    async signaturesByRepo(repoId) {
        if (repoId) {
            this.loading = true;
            const response = await this.axios.get('/repos?repo_id=' + repoId);
            this.users = response.data;
            this.loading = false;
        }
    },
      async signaturesByUser(userId) {
          if (userId) {
              this.loading = true;
              const response = await this.axios.get('/users?user_id=' + userId);
              this.users = response.data;
              this.loading = false;
          }
      }
  },
  async mounted() {
  }
};
</script>
