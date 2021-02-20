<template>
  <habits-table />
</template>

<script lang="ts">
import { Vue, Component } from 'nuxt-property-decorator';
import HabitsTable from '../components/habitsTable.vue';

@Component({
  components: {
    HabitsTable
  }
})
class Index extends Vue {
  get justifyValue(): string {
    return this.$mq === 'phone' ? 'center' : 'end';
  }
}

export default Index;
</script>

<style lang="scss" scoped>
.col--padding-no {
  padding: 0;
}
</style>
