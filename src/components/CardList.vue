<script>
import SingleCard from "./SingleCard.vue";
import data from "../data/store.js";
export default {
    props: {
        selectedArchetypes: String
    },
    name: "CardList",
    components: {
        SingleCard,
    },
    data() {
        return {
            data
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

        <div class="cardContainer">
            <div class="cardRows">
                <SingleCard v-for="element in data.cards" :immagine="element.card_images[0].image_url"
                    :nome="element.name" :tipo="element.type" v-show="selectedArchetypes == element.archetype" />
            </div>
        </div>

    </div>
</template>

<style scoped>
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