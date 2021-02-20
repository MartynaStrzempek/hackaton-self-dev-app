<template>
  <v-card
    elevation="12"
    class="card"
  >
    <v-navigation-drawer
      floating
      width="100%"
    >
      <v-list
        dense
        rounded
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </v-card>
</template>

<script lang="ts">
import { Vue, Component } from 'nuxt-property-decorator';

@Component
class Navigation extends Vue {
  items = [
    {
      title: 'Habits',
      icon: 'mdi-check'
    },
    {
      title: 'Statistics',
      icon: 'mdi-check'
    }
  ];
}

export default Navigation;
</script>

<style lang="scss" scoped>
.card {
  height: calc(100vh - 24px);
}
</style>
