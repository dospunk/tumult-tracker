<template>
  <div>
    <Die id="die"/>
    <main>
      <Expedition
        v-model:forest="heroForest"
        v-model:mountain="heroMountain"
        v-model:sea="heroSea"
        v-model:forest-selected="heroForestSelected"
        v-model:mountain-selected="heroMountainSelected"
        v-model:sea-selected="heroSeaSelected"
      />
      <div>
        <!-- placeholder -->
      </div>
      <Expedition
        v-model:forest="companionForest"
        v-model:mountain="companionMountain"
        v-model:sea="companionSea"
        v-model:forest-selected="companionForestSelected"
        v-model:mountain-selected="companionMountainSelected"
        v-model:sea-selected="companionSeaSelected"
      />
      <MovementMessage
        :top-player="{
          forest: heroForest,
          mountain: heroMountain,
          sea: heroSea,
          forestSelected: heroForestSelected,
          mountainSelected: heroMountainSelected,
          seaSelected: heroSeaSelected
        }"
        :bottom-player="{
          forest: enemyHeroForest,
          mountain: enemyHeroMountain,
          sea: enemyHeroSea,
          forestSelected: enemyHeroForestSelected,
          mountainSelected: enemyHeroMountainSelected,
          seaSelected: enemyHeroSeaSelected
        }"
      />
      <button id="reset-button" @click="reset">🔁</button>
      <MovementMessage
        :top-player="{
          forest: companionForest,
          mountain: companionMountain,
          sea: companionSea,
          forestSelected: companionForestSelected,
          mountainSelected: companionMountainSelected,
          seaSelected: companionSeaSelected
        }"
        :bottom-player="{
          forest: enemyCompanionForest,
          mountain: enemyCompanionMountain,
          sea: enemyCompanionSea,
          forestSelected: enemyCompanionForestSelected,
          mountainSelected: enemyCompanionMountainSelected,
          seaSelected: enemyCompanionSeaSelected
        }"
      />

      <Expedition
        v-model:forest="enemyHeroForest"
        v-model:mountain="enemyHeroMountain"
        v-model:sea="enemyHeroSea"
        v-model:forest-selected="enemyHeroForestSelected"
        v-model:mountain-selected="enemyHeroMountainSelected"
        v-model:sea-selected="enemyHeroSeaSelected"
      />
      <div>
        <!-- placeholder -->
      </div>
      <Expedition
        v-model:forest="enemyCompanionForest"
        v-model:mountain="enemyCompanionMountain"
        v-model:sea="enemyCompanionSea"
        v-model:forest-selected="enemyCompanionForestSelected"
        v-model:mountain-selected="enemyCompanionMountainSelected"
        v-model:sea-selected="enemyCompanionSeaSelected"
      />
    </main>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import Expedition from './components/Expedition.vue'
import MovementMessage from './components/MovementMessage.vue'
import Die from './components/Die.vue'

const heroForest = ref(0)
const heroMountain = ref(0)
const heroSea = ref(0)
const heroForestSelected = ref(true)
const heroMountainSelected = ref(true)
const heroSeaSelected = ref(true)

const companionForest = ref(0)
const companionMountain = ref(0)
const companionSea = ref(0)
const companionForestSelected = ref(true)
const companionMountainSelected = ref(true)
const companionSeaSelected = ref(true)

const enemyHeroForest = ref(0)
const enemyHeroMountain = ref(0)
const enemyHeroSea = ref(0)
const enemyHeroForestSelected = ref(true)
const enemyHeroMountainSelected = ref(true)
const enemyHeroSeaSelected = ref(true)

const enemyCompanionForest = ref(0)
const enemyCompanionMountain = ref(0)
const enemyCompanionSea = ref(0)
const enemyCompanionForestSelected = ref(true)
const enemyCompanionMountainSelected = ref(true)
const enemyCompanionSeaSelected = ref(true)

function reset() {
  heroForest.value = 0
  heroMountain.value = 0
  heroSea.value = 0
  companionForest.value = 0
  companionMountain.value = 0
  companionSea.value = 0
  enemyHeroForest.value = 0
  enemyHeroMountain.value = 0
  enemyHeroSea.value = 0
  enemyCompanionForest.value = 0
  enemyCompanionMountain.value = 0
  enemyCompanionSea.value = 0
  heroForestSelected.value = false
  heroMountainSelected.value = false
  heroSeaSelected.value = false
  companionForestSelected.value = false
  companionMountainSelected.value = false
  companionSeaSelected.value = false
  enemyHeroForestSelected.value = false
  enemyHeroMountainSelected.value = false
  enemyHeroSeaSelected.value = false
  enemyCompanionForestSelected.value = false
  enemyCompanionMountainSelected.value = false
  enemyCompanionSeaSelected.value = false
}
</script>

<style scoped>
main {
  display: grid;
  grid-template-columns: auto min-content auto;
  grid-template-columns: auto min-content auto;
  justify-content: space-evenly;
	justify-items: center;
}

#reset-button {
  font-size: 25px;
}

#die {
  position: absolute;
  left: 5px;
  top: 47%;
  bottom: 47%;
	width: 4%;
	font-size: 20px;
}
</style>
