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
            <v-list dense>
              <v-list-item  v-for="(signature, index) in signatures " :key="index">
                <v-list-item-content>
                  <signature :signature="signature" style="width: 100%"></signature>
                </v-list-item-content>
              </v-list-item>
            </v-list>

          </div>
        </v-container>
    </v-content>
  </v-app>
</template>

<script>
import Signature from './components/Signature';
import SearchBar from './components/SearchBar';

export default {
  name: 'App',

  components: {
    Signature,
      SearchBar,
  },

  data: () => ({
    signatures: [],
      loading: false
  }),
  methods: {
    async signaturesByRepo(repoId) {
        if (repoId) {
            this.loading = true;
            const response = await this.axios.get('/repos?repo_id=' + repoId);
            this.signatures = response.data;
            this.loading = false;
        }
    },
      async signaturesByUser(userId) {
          if (userId) {
              this.loading = true;
              const response = await this.axios.get('/users?user_id=' + userId);
              this.signatures = response.data;
              this.loading = false;
          }
      }
  },
  async mounted() {
  }
};
</script>
