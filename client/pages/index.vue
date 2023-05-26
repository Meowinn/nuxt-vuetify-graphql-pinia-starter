<template>
	<v-app>
		<PokemonCard
			v-for="pokemon in data.pokemon_v2_pokemon"
			:id="pokemon.id"
			:key="pokemon.id"
			:name="pokemon.name"
			:weight="pokemon.weight"
			:height="pokemon.height"
			:data="pokemon.pokemon_v2_pokemonforms"
		/>

		<!-- <pre>{{ data.pokemon_v2_pokemon[0].pokemon_v2_pokemonforms[0].pokemon_v2_pokemonformsprites[0].sprites}}</pre> -->
	</v-app>
</template>

<script lang="ts" setup>
type PokemonResults = {
	pokemon_v2_pokemon: {
		results: {
			id: Number
			name: String
			height: Number
			weight: Number
			base_experience: Number
		}[]
	}
}

const query = gql`
	query getPokemon($limit: Int) {
		pokemon_v2_pokemon(limit: 10) {
			id
			name
			height
			weight
			base_experience
			pokemon_v2_pokemonforms {
				pokemon_v2_pokemonformsprites {
					sprites
				}
			}
		}
	}
`

const { data } = await useAsyncQuery<PokemonResults>(query)

console.log(data)
</script>
