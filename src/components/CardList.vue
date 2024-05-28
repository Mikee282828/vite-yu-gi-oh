<script>
import SingleCard from "./SingleCard.vue";
import data from "../data/store.js";
export default {
    name: "CardList",
    components: {
        SingleCard,
    },
    data() {
        return {
            data,
        }
    },
    methods: {
        foundCardsNumber() {
            return data.selected.length;
        }
    },
    mounted() {

    }
}
</script>

<template>
    <div class="container">

        <div class="cardContainer">
            <div class="found">
                <h2>Found {{ foundCardsNumber() }} cards</h2>
            </div>
            
            <div class="cardRows">
                <SingleCard v-for="element in data.selected" :immagine="element.card_images[0].image_url"
                    :nome="element.name" :tipo="element.type"/>
            </div>
        </div>

    </div>
</template>

<style scoped>
.found {
    background-color: #222;
    color: white;
    padding: 1rem;
}

.container {
    padding: 3rem;
}

.cardContainer {
    padding: 2rem;
    background-color: white;
}

.cardRows {
    display: flex;
    flex-flow: row wrap;
    gap: calc(5% / 4);
}
</style>