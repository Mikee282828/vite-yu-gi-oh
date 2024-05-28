<script>
import CardList from "./components/CardList.vue";
import AppHeader from "./components/AppHeader.vue";
import store from "./data/store.js";
import axios from "axios";
export default {
  components: {
    CardList,
    AppHeader
  },
  data() {
    return {
      store,
      archetipo:"Dark Magician"
    }
  },
  methods: {
    getCard() {
      axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=10&offset=0").then(
        (result) => {
          this.store.cards = result.data.data;
        });
    },
    getArchetype() {
      axios.get("https://db.ygoprodeck.com/api/v7/archetypes.php").then(
        (result) => {
          this.store.archetypes = result.data;
          // console.log(this.store.archetypes[0].archetype_name);
        }
      )
    },
    getSelected() {
        axios.get(`https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=${this.archetipo}`).then(
          (result) => {
            store.selected = result.data.data;
          }
        );
      }
  },
  created() {
    this.getCard();
    this.getArchetype();
  }
}
</script>

<template>

  <AppHeader />

  <div class="selezione">
    <select name="archetipo" id="archetype" v-model="archetipo" :input="getSelected()">
      <option v-for="object in this.store.archetypes" :value="object.archetype_name">{{ object.archetype_name }}
      </option>
    </select>
  </div>

  <CardList />

</template>


<style scoped>
select {
  padding: 1rem;
  margin: 3rem 0 0 3rem;
  font-size: 1rem;
}
</style>