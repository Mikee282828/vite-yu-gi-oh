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
    }
  },
  methods: {
  },
  // created() {
  //   axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=15").then(
  //     (result) => {
  //       for (const iterator of result.data.data) {
  //         this.store.card.push(iterator);
  //       }
  //     });
  //   console.log(store);
  // }
  created() {
    axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=15").then(
      (result) => {
        this.store.cards = result.data.data
      });
  }
}
</script>

<template>
  <AppHeader />
  <CardList />

</template>

<style></style>