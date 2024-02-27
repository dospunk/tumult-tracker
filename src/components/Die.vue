<template>
	<button @click="rollADie"> 🎲 </button>
</template>

<script lang="ts" setup>
function rollADie(){
	const result = Math.ceil(Math.random()*6)
	alert(result)
}
</script>