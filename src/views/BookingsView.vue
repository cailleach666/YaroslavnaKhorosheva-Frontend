<template>
  <div class="calender-container">
    <n-calendar v-model:value="value" #="{ year, month, date }" :is-date-disabled="isDateDisabled"
      @update:value="handleUpdateValue">
      {{ year }}-{{ month }}-{{ date }}
    </n-calendar>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import { useMessage } from 'naive-ui'
import { isYesterday, addDays } from 'date-fns/esm'
import { NCalendar } from "naive-ui";




export default defineComponent({
  components: { NCalendar },
  setup() {
    const message = useMessage()
    return {
      value: ref(addDays(Date.now(), 1).valueOf()),
      handleUpdateValue(
        _: number,
        { year, month, date }: { year: number; month: number; date: number }
      ) {
        message.success(`${year}-${month}-${date}`)
      },
      isDateDisabled(timestamp: number) {
        if (isYesterday(timestamp)) {
          return true
        }
        return false
      }
    }
  }
})
</script>

<style>
.calender-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  overflow: auto;

}

.n-calendar {
  min-width: 10rem;
}
</style>