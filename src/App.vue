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
      archetipo: null
    }
  },
  methods: {
  },
  created() {
    axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=500&offset=0").then(
      (result) => {
        this.store.cards = result.data.data;
      });
    axios.get("https://db.ygoprodeck.com/api/v7/archetypes.php").then(
      (result) => {
        this.store.archetypes = result.data;
        // console.log(this.store.archetypes[0].archetype_name);
      }
    )
  }
}
</script>

<template>

  <AppHeader />

  <div class="selezione">
    <select name="archetipo" id="archetype" v-model="archetipo">
      <option value="myAll"> All 
      </option>
      <option v-for="object in this.store.archetypes" :value="object.archetype_name">{{ object.archetype_name }}
      </option>
    </select>
  </div>
  
  <CardList :selectedArchetypes="archetipo" />

</template>


<style scoped>
select {
  padding: 1rem;
  margin:3rem 0 0 3rem;
}
</style>