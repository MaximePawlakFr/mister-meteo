<script setup>
import { ref, watch } from "vue"
import { drawPlot } from "../utils/plotly"

const props = defineProps({
  data: {
    type: Object,
    default: () => {
      return {}
    }
  },
  dates: {
    type: Array,
    default: () => {
      return []
    }
  },
  dateColumn: String,
  stationColumns: Array,
  title: String
})

const graph = ref(null)

watch(props, (a, b) => {
  const { data, dates, dateColumn, stationColumns, title } = b
  if (data && dates && dateColumn && stationColumns && title) {
    setTimeout(() => {
      drawPlot(graph.value, data, dates, dateColumn, stationColumns, title)
    }, 100)
  }
})
</script>
<template>
  <div ref="graph" class="h-75-vh"></div>
</template>
