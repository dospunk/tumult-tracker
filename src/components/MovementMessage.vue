<template>
  <p v-if="topMovesForward && bottomMovesForward">Both Advance</p>
  <p v-else-if="bottomMovesForward">🔽 Advances</p>
  <p v-else-if="topMovesForward">🔼 Advances</p>
  <p v-else>Neither Advance</p>
</template>

<script lang="ts" setup>
import { computed } from 'vue'
import type { PropType } from 'vue'

type PlayerData = {
  mountain: number
  forest: number
  sea: number
  mountainSelected: boolean
  forestSelected: boolean
  seaSelected: boolean
}

const props = defineProps({
  topPlayer: { type: Object as PropType<PlayerData>, required: true },
  bottomPlayer: { type: Object as PropType<PlayerData>, required: true }
})

const topMovesForward = computed(() => {
  const winsMountain =
    props.topPlayer.mountainSelected && props.topPlayer.mountain > props.bottomPlayer.mountain
  const winsForest =
    props.topPlayer.forestSelected && props.topPlayer.forest > props.bottomPlayer.forest
  const winsSea = props.topPlayer.seaSelected && props.topPlayer.sea > props.bottomPlayer.sea
  return winsMountain || winsForest || winsSea
})

const bottomMovesForward = computed(() => {
  const winsMountain =
    props.bottomPlayer.mountainSelected && props.topPlayer.mountain < props.bottomPlayer.mountain
  const winsForest =
    props.bottomPlayer.forestSelected && props.topPlayer.forest < props.bottomPlayer.forest
  const winsSea = props.bottomPlayer.seaSelected && props.topPlayer.sea < props.bottomPlayer.sea
  return winsMountain || winsForest || winsSea
})
</script>
