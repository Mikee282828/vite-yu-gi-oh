<script>
import CardList from "./components/CardList.vue";
import AppHeader from "./components/AppHeader.vue";
import store from "./data/store.js"
export default {
  components: {
    CardList,
    AppHeader
  },
  data() {
    return {
      store,
      prova : []
    }
  },
  methods: {
  },
  created() {
    axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=15").then(
      (result) => {
        for (const iterator of result.data.data) {
          this.store.push(iterator);
        }
      });
  }
}
</script>

<template>
  <AppHeader />
  <CardList />

</template>

<style></style>