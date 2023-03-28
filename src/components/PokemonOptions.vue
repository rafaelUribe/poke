<template>
<div class="options-container container">
  <div class="row justify-content-center">
    <div class="col-md-4">
      <div class="card">
        <div class="card-header">
          <h5 class="card-title">Opciones:</h5>
        </div>
        <div class="card-body">
          <div class="list-group">
            <a href="#" class="list-group-item list-group-item-action" v-for="pokemon in pokemons" :key="pokemon.id" @click="$emit('selection', pokemon.id)">
              {{ pokemon.name }}
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
    props: {
        pokemons: {
            type: Array,
            required: true
        }
    }
}
</script>

<style scoped>
ul {
    list-style-type: none;
}
li {
    background-color: white;
    border-radius: 5px;
    border: 1px solid rgba(0, 0, 0, 0.2);
    cursor: pointer;
    margin-bottom: 10px;
    width: 250px;
}

li:hover {
    background-color: rgba(0, 0, 0, 0.05);
}

.options-container {
    margin-top: 250px;
}
</style>
