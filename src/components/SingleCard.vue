<script>
export default {
    props: {
        immagine: String,
        nome: String,
        tipo: String
    },
    name: "SingleCard",
    data() {
        return {

        }
    },
    methods: {
    },
    mounted() {
    }
}
</script>

<template>
    <div class="card">
        <img :src="immagine" alt="carta">
        <div class="info">
            <h2>
                {{ nome }}
            </h2>
            <h3>
                {{ tipo }}
            </h3>
        </div>
    </div>
</template>

<style scoped>
.card {
    width: 19%;
    text-align: center;
    background-color: yellowgreen;
}

[alt="carta"] {
    width: 100%;
}

.info {
    padding-top: 1rem;
    height: 10rem;
}

h2 {
    color: white;
    margin-bottom: 1rem;
}
</style>