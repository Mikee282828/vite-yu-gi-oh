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
      store
    }
  },
  methods: {
  },
  created() {
    console.log(this.store);
    axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=10&offset=0").then(
      (result) => {
        this.store = result.data.data;
        console.log(this.store);
      });
    console.log(this.store);
  }
}
</script>

<template>
  <AppHeader />
  <CardList />

</template>

<style></style>