<script>
export default {
    props: {
        immagine: String
    },
    name: "SingleCard",
    data() {
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
    </div>
</template>

<style>
.card {
    width: 20%;
}

[alt="carta"] {
    width: 100%;
}
</style>