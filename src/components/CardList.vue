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
            data,
            nOfFound: 0
        }
    },
    methods: {
        foundCardsNumber() {
            this.nOfFound = 0;
            let counter = 0;
            for (const iterator of data.cards) {
                if (iterator.archetype == this.selectedArchetypes) {
                    this.nOfFound++;
                }
                counter++
            }
            if (this.selectedArchetypes == "myAll") {
                this.nOfFound = counter;
            }
            return this.nOfFound;
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
                <SingleCard v-for="element in data.cards" :immagine="element.card_images[0].image_url"
                    :nome="element.name" :tipo="element.type"
                    v-show="selectedArchetypes == element.archetype || selectedArchetypes == `myAll`" />
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