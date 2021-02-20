<template>
  <v-app dark>
    <h1 v-if="error.statusCode === 404">
      {{ pageNotFound }}
    </h1>
    <h1 v-else>
      {{ otherError }}
    </h1>
    <NuxtLink to="/">
      Home page
    </NuxtLink>
  </v-app>
</template>

<script lang="ts">
import { Vue, Component, Prop } from 'nuxt-property-decorator';

@Component({
  layout: 'empty',
  head() {
    const title =
      this.error.statusCode === 404 ? this.pageNotFound : this.otherError;
    return {
      title
    }
  }
})
class ErrorPage extends Vue {
  @Prop({ default: '' }) error: string;

  pageNotFound = '404 Not Found';
  otherError = 'An error occurred';
}

export default ErrorPage;
</script>

<style scoped>
h1 {
  font-size: 20px;
}
</style>
