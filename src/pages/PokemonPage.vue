<template>
    <h1 v-if="!pokemon">Espere por favor ...</h1>
    <div v-else>
        <h1>
            ¿Quién es este pokémon?
        </h1>

        <PokemonPicture :pokemonId="pokemon.id" :showPokemon="showPokemon"/>
        <div v-if="showAnswer" class="fade-in message">
            <h2>{{message}}</h2>
            <button @click="newGame">Nuevo juego</button>
        </div>
        <PokemonOptions
                :pokemons="pokemonArr"
                @selection="checkAnswer"
        />


    </div>
</template>

<script>
    import PokemonPicture from "../components/PokemonPicture";
    import PokemonOptions from "../components/PokemonOptions";

    import getPokemonOptions from "@/helpers/getPokemonOptions";



    export default {
        name: 'PokemonPage',
        components: {
            PokemonPicture,
            PokemonOptions,
        },
        data(){
            return{
                pokemonArr: [],
                pokemon: null,
                showPokemon: false,
                showAnswer: false,
                message: ''
            }
        },
        methods: {
         async mixPokemonArray(){
                this.pokemonArr = await getPokemonOptions()

                const rndInt = Math.floor(Math.random()*4)

                this.pokemon = this.pokemonArr[rndInt]

            },
            checkAnswer(selectedId){

                this.showPokemon = true
                this.showAnswer = true

                if (selectedId === this.pokemon.id){
                    this.message =
                        `Correcto, ${this.pokemon.name.toUpperCase()}`
                } else {
                    this.message = `Oops, era ${this.pokemon.name.toUpperCase()}`
                }
            },
            newGame(){
                this.showPokemon = false
                this.showAnswer = false
                this.pokemonArr = []
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
    h1, h2 {
        color: white;
    }

    h2{
        font-size: 32px;
    }

    button {
        border-radius: 24px;
        border: none;
        color: white;
        font-weight: bold;
        font-size: 18px;
        text-transform: capitalize;
        padding: 12px 24px;
        cursor: pointer;
        margin-bottom: 10px;
        width: 180px;
        transition: all .5s ease;
        -webkit-tap-highlight-color: transparent;
        -webkit-box-shadow: 10px 10px 20px -6px rgba(42, 218, 187, 0.85);
        -moz-box-shadow: 10px 10px 20px -6px rgba(42, 218, 187, 0.85);
        box-shadow: 10px 10px 20px -6px rgba(42, 218, 187, 0.85);
        background: #2adabb;  /* fallback for old browsers */
        background: -webkit-linear-gradient(to right, #10c4c7, #2adabb);  /* Chrome 10-25, Safari 5.1-6 */
        background: linear-gradient(to right, #10c4c7, #2adabb); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

    }

    button:hover {
        -webkit-box-shadow: 10px 10px 97px -12px rgba(42, 218, 187, 0.85);
        -moz-box-shadow: 10px 10px 97px -12px rgba(42, 218, 187, 0.85);
        box-shadow: 10px 10px 97px -12px rgba(42, 218, 187, 0.85);

        background: #2adabb;  /* fallback for old browsers */
        background: -webkit-linear-gradient(to right, #10c4c7, #2adabb);  /* Chrome 10-25, Safari 5.1-6 */
        background: linear-gradient(to right, #10c4c7, #2adabb); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
    }

    @media (max-width: 768px) {
        .message {
            margin-bottom: 40px;
        }


    }

</style>

