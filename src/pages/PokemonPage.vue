<template>
    <h1 v-if="!pokemon">Espere...</h1>

    <div v-else>
        <h1>¿Quién es este pokemón?</h1>
        <PokemonPicture :pokemonId="pokemon.id" :showPokemon="showPokemon"/>
        <PokemonOptions :pokemons="pokemonArr" @selection="checkAnswer( $event)"/>
        <div v-if="showAnswer" class="my-4">
            <h2 class="fade-in">{{message}}</h2>
            <button class="btn btn-primary"
                @click="newGame()"
            >Nuevo juego</button>
        </div>
    </div>
</template>

<script>
import PokemonOptions from "@/components/PokemonOptions.vue";
import PokemonPicture from "@/components/PokemonPicture.vue";

import getPokemonOptions from '@/helpers/getPokemonOptions'

export default {
    components: {PokemonOptions, PokemonPicture},
    data() {
        return {
            pokemonArr: [],
            pokemon: null,
            showPokemon: false,
            showAnswer: false,
            message: '',
        }
    },
    methods: {
        async mixPokemonArray(){
            this.pokemonArr = await getPokemonOptions()
            
            const rndInt = Math.floor( Math.random() * 4)
            this.pokemon = this.pokemonArr[rndInt]
        },
        checkAnswer( pokemonId ) {
            this.showPokemon = true
            this.showAnswer = true

            if(this.pokemon.id === pokemonId) {
                this.message = `Correcto, ${ this.pokemon.name }`    
            } else {
                this.message = `Oops, era ${ this.pokemon.name }`
            };
        },
        newGame(){
            this.showAnswer = false
            this.showPokemon = false
            this.pokemon = null
            this.mixPokemonArray()
        }
    },
    mounted() {
        this.mixPokemonArray()
    }
}

</script>

<style>

</style>
