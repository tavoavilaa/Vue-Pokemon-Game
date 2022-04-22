<template>
    <div class="options-container">
        <ul>
            <li
                v-for="pokemon in pokemons"
                :key="pokemon.id"
                @click="$emit( 'selection', pokemon.id  )"
            >
                {{pokemon.name}}
            </li>

        </ul>
    </div>
</template>

<script>
    export default {
        name: "PokemonOptions",
        props: {
            pokemons: {
                type: Array,
                required: true
            }
        }
    }
</script>

<style scoped>
    /* Pokemon Options */
    ul {
        list-style-type: none;
        background: white;
        padding: 40px;
        border-radius: 24px;
        width: 30%;
        display: grid;
        grid-template-columns: 1fr 1fr;
        row-gap: 24px;
        place-items: center;
        justify-content: center;
        align-items: center;

        -webkit-tap-highlight-color: transparent;
        -webkit-box-shadow: 10px 10px 20px -6px rgba(255,104,121,0.85);
        -moz-box-shadow: 10px 10px 20px -6px rgba(255,104,121,0.85);
        box-shadow: 10px 10px 20px -6px rgba(255,104,121,0.85);
    }
    li {
        border-radius: 24px;
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
        -webkit-box-shadow: 10px 10px 20px -6px rgba(255,104,121,0.85);
        -moz-box-shadow: 10px 10px 20px -6px rgba(255,104,121,0.85);
        box-shadow: 10px 10px 20px -6px rgba(255,104,121,0.85);
        background: #ff6879;  /* fallback for old browsers */
        background: -webkit-linear-gradient(to right, #FEAB7B, #ff6879);  /* Chrome 10-25, Safari 5.1-6 */
        background: linear-gradient(to right, #FEAB7B, #ff6879); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

    }

    li:hover {
        -webkit-box-shadow: 10px 10px 97px -12px rgba(255,104,121,0.85);
        -moz-box-shadow: 10px 10px 97px -12px rgba(255,104,121,0.85);
        box-shadow: 10px 10px 97px -12px rgba(255,104,121,0.85);

        background: #ff6879;  /* fallback for old browsers */
        background: -webkit-linear-gradient(to right, #ffb78d, #ff6879);  /* Chrome 10-25, Safari 5.1-6 */
        background: linear-gradient(to right, #ffb78d, #ff6879); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
    }



    .options-container {
        display: flex;
        justify-content: center;}


    @media (max-width: 768px) {
        ul {
            width: 100%;
            grid-template-columns: 1fr;
            margin: 24px;
        }


    }



</style>