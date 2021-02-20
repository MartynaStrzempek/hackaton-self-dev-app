<template>
  <v-app dark>
    <v-main>
      <v-container fluid class="ma-0">
        <v-row>
          <v-col cols="12" sm="4" md="3">
            <navigation />
          </v-col>
          <v-col cols="12" sm="8" md="9" class="col--padding-no">
            <nuxt />
          </v-col>
        </v-row>
      </v-container>
    </v-main>
    <v-footer>
      <span class="footer text-center">Bubdzie company &copy; 2021</span>
    </v-footer>
  </v-app>
</template>

<script lang="ts">
import { Vue, Component } from 'nuxt-property-decorator';
import Navigation from '../components/navigation.vue';

@Component({
  components: {
    Navigation
  }
})
class DefaultLayout extends Vue {
}

export default DefaultLayout;
</script>

<style lang="scss">
.footer {
  width: 100%;
}
</style>
