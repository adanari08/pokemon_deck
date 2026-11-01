
<script setup>
import { ref, onMounted } from 'vue'
import PokemonCard from './components/PokemonCard.vue'

const pokemones = ref([])
const cargando = ref(true)
const error = ref('')

async function cargarPokemones() {
  cargando.value = true
  error.value = ''
  pokemones.value = []

  const idsUsados = new Set()

  try {
    while (pokemones.value.length < 40) {
      const faltantes = 40 - pokemones.value.length
      const ids = []

      // Elegir números aleatorios sin repetir
      while (ids.length < faltantes) {
        const id = Math.floor(Math.random() * 649) + 1

        if (!idsUsados.has(id)) {
          idsUsados.add(id)
          ids.push(id)
        }
      }

      // Consultar los Pokémon en la API
      const datos = await Promise.all(
        ids.map(async (id) => {
          const respuesta = await fetch(
            `https://pokeapi.co/api/v2/pokemon/${id}`
          )

          if (!respuesta.ok) {
            throw new Error('No se pudo obtener un Pokémon')
          }

          return respuesta.json()
        })
      )

      // Elegir Pokémon con imagen y al menos 4 movimientos
      const validos = datos.filter(pokemon =>
  pokemon.abilities.length >= 2 &&
  pokemon.moves.length >= 4 &&
  pokemon.sprites.other['official-artwork'].front_default
)

      pokemones.value.push(...validos)
    }
  } catch (e) {
    error.value = 'No se pudieron cargar los Pokémon. Intenta nuevamente.'
  } finally {
    cargando.value = false
  }
}

onMounted(cargarPokemones)
</script>

<template>
  <main>
    <h1>Mi Deck Pokémon</h1>
    <p>40 cartas Pokémon aleatorias</p>

    <button @click="cargarPokemones">
      Generar otro deck
    </button>

    <p v-if="cargando">Cargando cartas Pokémon...</p>
    <p v-if="error">{{ error }}</p>

    <div class="deck">
      <pokemon-card
        v-for="pokemon in pokemones"
        :key="pokemon.id"
        :pokemon="pokemon"
      />
    </div>
  </main>
</template>

<style>
body {
  margin: 0;
  display: block;
  background: #f1f1f1;
  font-family: Arial, sans-serif;
  color: #222;
}

#app {
  max-width: none;
  margin: 0;
  padding: 0;
  text-align: center;
}

main {
  padding: 25px;
}


h1 {
  color: #a64b70;
  font-size: 30px;
}

button {
  background: #c77796;
  color: white;
  border: none;
  padding: 10px 18px;
  border-radius: 8px;
  cursor: pointer;
  margin: 15px;
}

button:hover {
  background: #ad5b7c;
}



.deck {
  display: grid;
  grid-template-columns: repeat(auto-fit, 250px);
  gap: 16px;
  justify-content: center;
  max-width: 1400px;
  margin: 20px auto;
  text-align: left;
}

</style>
