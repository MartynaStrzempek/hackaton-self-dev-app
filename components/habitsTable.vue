<template>
  <v-simple-table>
    <thead>
      <tr>
        <th class="pa-1 text-center">
          {{ getYesterdayDate() }}
        </th>
        <th class="pa-1 text-center">
          {{ getTodayDate() }}
        </th>
        <th class="pa-2">
          Name
        </th>
        <th class="pa-1 text-center">
          Week
        </th>
        <th class="pa-1 text-center">
          Month
        </th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(habit, idx) in habitsMock" :key="idx">
        <td class="pa-1 text-center">
          <v-icon :color="getStateIconColor(habit.yesterdayState)">
            {{ getStateIconName(habit.yesterdayState) }}
          </v-icon>
        </td>
        <td class="pa-1 text-center">
          <v-icon :color="getStateIconColor(habit.todayState)">
            {{ getStateIconName(habit.todayState) }}
          </v-icon>
        </td>
        <td class="pa-2">
          {{ habit.title }}
        </td>
        <td class="pa-1 text-center">
          {{ habit.weekSuccessAmount }} / {{ daysInWeek }}
        </td>
        <td class="pa-1 text-center">
          {{ habit.monthSuccessAmount }} / {{ getAmountOfDaysInCurrentMonth() }}
        </td>
      </tr>
    </tbody>
  </v-simple-table>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator';
import { habitsMock } from '../static/habitsMock';
import { HABIT_STATE, HABIT_STATE_COLORS, HABIT_STATE_ICONS } from '../types/types';

@Component({
  data() {
    return {
      habitsMock
    }
  }
})
class HabitsTable extends Vue {
  daysInWeek = 7;

  getStateIconName(currentDayState: HABIT_STATE): HABIT_STATE_ICONS {
    return HABIT_STATE_ICONS[currentDayState];
  };

  getStateIconColor(currentDayState: HABIT_STATE): HABIT_STATE_COLORS {
    return HABIT_STATE_COLORS[currentDayState];
  };

  getYesterdayDate(): string {
    const date = new Date();
    date.setDate(date.getDate() - 1);
    return `${date.getDate()}.${date.getMonth() + 1}`;
  };

  getTodayDate(): string {
    const todayDate = new Date();
    return `${todayDate.getDate()}.${todayDate.getMonth() + 1}`;
  };

  getAmountOfDaysInCurrentMonth(): number {
    const currentYear = new Date().getFullYear();
    const currentMonth = new Date().getMonth() + 1;
    return new Date(currentYear, currentMonth, 0).getDate();
  };
}
export default HabitsTable;
</script>

<style lang="scss" scoped>

</style>
