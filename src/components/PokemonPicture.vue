<template>
    <div class="main-cont">
        <div class="pokemon-container">
            <img :src="this.imgSrc"
                class="hidden-pokemon"
                alt="pokemon">
            <img v-if="showPokemon" 
                :src="this.imgSrc"
                class="fade-in"
                alt="pokemon">
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                
                }
        },
        props: {
            pokemonId: {
                type: Number,
                required: true
            },
            showPokemon: {
                type: Boolean,
                required: true,
                default: false
            }
        },
        computed: {
            imgSrc(){
                return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`
            }
        },
    }
</script>

<style scoped>
    .main-cont{
        display: flex;
        justify-content: center;
    }
    .pokemon-container {
        display: flex;
        align-items: center;
        justify-content: center;
    }
    img {
        height: 200px;
        top: 130px;
        position: absolute;
        margin: 0 auto;
        user-select: none;
        -moz-user-select: none;
        -ms-user-select: none;
        -webkit-user-drag: none;
        -webkit-user-select: none;
    }
    .hidden-pokemon {
        filter: brightness(0);
    }
</style>
