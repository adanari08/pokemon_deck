
<script setup>
defineProps(['pokemon'])
</script>

<template>
  <div class="pokemon-card carta-rosa">
    <div class="encabezado">
      <h2>{{ pokemon.name }}</h2>
      <span>HP {{ pokemon.stats[0].base_stat }}</span>
    </div>

    <div class="imagen">
      <img
        :src="pokemon.sprites.other['official-artwork'].front_default"
        :alt="pokemon.name"
      />
    </div>

    <p class="numero">Pokémon #{{ pokemon.id }}</p>

    <p>
  <strong>Tipo:</strong>
  {{ pokemon.types.map(tipo => tipo.type.name).join(', ') }}
</p>

    <p><strong>Altura:</strong> {{ pokemon.height / 10 }} m</p>
    <p><strong>Peso:</strong> {{ pokemon.weight / 10 }} kg</p>

    <p>
      <strong>Habilidades especiales:</strong>
      {{ pokemon.abilities.map(a => a.ability.name).join(', ') }}
    </p>

    <h3>4 ataques</h3>

    <div
      v-for="(ataque, index) in pokemon.moves.slice(0, 4)"
      :key="index"
      class="ataque"
    >
      <span>{{ ataque.move.name }}</span>
     
    </div>
  </div>
</template>


<style scoped>
.pokemon-card {
  width: 250px;
  padding: 12px;
  box-sizing: border-box;
}

.carta-rosa {
  background: linear-gradient(#fce6ec, #f3c6d4);
  border: 5px solid #d990a9;
  border-radius: 14px;
  box-shadow: 0 3px 8px #00000025;
  color: #442737;
}

/* Nombre y HP */
.encabezado {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.encabezado h2 {
  font-size: 18px;
  margin: 5px 0;
  text-transform: capitalize;
}

.encabezado span {
  font-size: 13px;
  font-weight: bold;
  color: #b83f6d;
}

/* Imagen */
.imagen {
  background-color: #fff3f7;
  border-radius: 8px;
  padding: 5px;
  text-align: center;
}

.imagen img {
  width: 100%;
  height: 135px;
  object-fit: contain;
  background-color: #fff3f7;
  border: 2px solid #d990a9;
  border-radius: 6px;
}

/* Información del Pokémon */
.pokemon-card p {
  font-size: 12px;
  margin: 7px 0;
  line-height: 1.3;
}

.numero {
  text-align: center;
  font-style: italic;
}

/* Ataques */
.pokemon-card h3 {
  font-size: 14px;
  margin: 12px 0 6px;
}

.ataque {
  font-size: 12px;
  padding: 4px 0;
  border-bottom: none;
}
</style>

