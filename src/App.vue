<template>
  <div class="container">
    <div class="row">
      <h1>Clash Royale Cards</h1>

      <input
        type="text"
        class="form-control bg-dark text-light rounded-0 border-0 my-4"
        placeholder="Search Card"
        @keyup="searchCard()"
        v-model="textSearch"
      />

      <table class="table table-dark table-hover">
        <thead>
          <tr>
            <th v-for="title in titles" :key="title">
              {{ title }}
            </th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(card, index) in filteredCards" :key="card.id">
            <td class="text-muted">
              {{ index + 1 }}
            </td>
            <td>
              {{ card.name }}
            </td>
            <td>
              {{ card.elixir }}
            </td>
            <td>
              {{ card.rarity }}
            </td>
            <td>
              {{ card.arena }}
            </td>
            <td>
              {{ card.description }}
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      cards: [],
      filteredCards: [],
      titles: ["#", "Name", "Elixir", "Rarity", "Arena", "Description"],
      textSearch: ''
    };
  },
  async mounted() {
    const res = await fetch(
      "https://royaleapi.github.io/cr-api-data/json/cards_i18n.json"
    );
    const data = await res.json();
    console.log(data);
    this.cards = data;
    this.filteredCards = data
  },
  methods: {

    searchCard() {
    this.filteredCards = this.cards.filter(card => card.name.toLowerCase().includes(this.textSearch.toLowerCase()))
    },

  },
};
</script>

<style>
</style>
