<script lang="ts" setup>
const sprites = computed(() => props.data[0].pokemon_v2_pokemonformsprites[0].sprites)
</script>

<template>
	<v-card class="mx-auto my-12">
		<v-card-title>{{ id }}. {{ name }}</v-card-title>
		<v-chip>Weight: {{ weight }}</v-chip>
		<v-chip>Height: {{ height }}</v-chip>
		<pre>{{ sprites }}</pre>
	</v-card>
</template>
