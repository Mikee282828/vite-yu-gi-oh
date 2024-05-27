<script>
import SingleCard from "./SingleCard.vue";
import lista from "../data/store.js";
export default {
    name: "CardList",
    components: {
        SingleCard,
    },
    data() {
        return {
            lista
        }
    },
    methods: {

    },
    mounted() {

    }
}
</script>

<template>
    <div class="container">

        <select name="" id="">
            <option value="Uno">Uno</option>
        </select>

        <div class="cardContainer">
            <div class="cardRows">
                <SingleCard v-for="element in lista" :immagine="element.card_images[0].image_url_small" />
            </div>
        </div>

    </div>
</template>

<style>
.container {
    padding: 3rem;
    background-color: yellowgreen;
}

.cardContainer {
    padding: 2rem;
    background-color: white;
}

.cardRows {
    display: flex;
    flex-flow: row wrap;
}
</style>