<template>
  <section>
    <div class="terrain-container forest">
      <button @click="$emit('update:forest', forest + 1)">🔼</button>
      <div>{{ forest }}</div>
      <label
        >🌲
        <input
          :checked="forestSelected"
          @change="$emit('update:forestSelected', !forestSelected)"
          type="checkbox"
        />
      </label>
      <button @click="$emit('update:forest', forest - 1)">🔽</button>
    </div>

    <div class="terrain-container mountain">
      <button @click="$emit('update:mountain', mountain + 1)">🔼</button>
      <div>{{ mountain }}</div>
      <label
        >⛰️
        <input
          :checked="mountainSelected"
          @change="$emit('update:mountainSelected', !mountainSelected)"
          type="checkbox"
        />
      </label>
      <button @click="$emit('update:mountain', mountain - 1)">🔽</button>
    </div>

    <div class="terrain-container sea">
      <button @click="$emit('update:sea', sea + 1)">🔼</button>
      <div>{{ sea }}</div>
      <label
        >🌊
        <input
          :checked="seaSelected"
          @change="$emit('update:seaSelected', !seaSelected)"
          type="checkbox"
        />
      </label>
      <button @click="$emit('update:sea', sea - 1)">🔽</button>
    </div>
  </section>
</template>

<script lang="ts" setup>
const props = defineProps({
  mountain: { type: Number, required: true },
  forest: { type: Number, required: true },
  sea: { type: Number, required: true },
  forestSelected: { type: Boolean, required: true },
  mountainSelected: { type: Boolean, required: true },
  seaSelected: { type: Boolean, required: true }
})
defineEmits([
  'update:mountain',
  'update:forest',
  'update:sea',
  'update:forestSelected',
  'update:mountainSelected',
  'update:seaSelected'
])
</script>

<style scoped>
section {
  display: flex;
  flex-direction: row;
	justify-content: space-around;
}

.terrain-container {
  display: flex;
  align-items: center;
  flex-direction: column;
	font-size: 20px;
	padding: 5px;
}

.terrain-container:has(label > input[type="checkbox"]:not(:checked)){
	opacity: 60%;
}

.terrain-container > label > input {
	display: none;
}

button {
  border: none;
  background-color: inherit;
	font-size: inherit;
}

.forest {
  background-color: green;
}

.mountain {
  background-color: orange;
}

.sea {
  background-color: lightblue;
}
</style>
