<template>
  <div class="container">
    <div class="row">
      <table class="table table-dark table-hover">
        <thead>
          <tr>
            <th>Cards</th>
            <th>Elixir</th>
            <th>Type</th>
            <th>Rarity</th>
            <th>Arena</th>
            <th>Description</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="card in cards" :key="card.id">
            <td>
              {{ card.name }}
            </td>
            <td>
              {{ card.elixir }}
            </td>
            <td>
              {{ card.type }}
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
    };
  },
  async mounted() {
    const res = await fetch(
      "https://royaleapi.github.io/cr-api-data/json/cards.json"
    );
    const data = await res.json();
    console.log(data);
    this.cards = data;
  },
};
</script>

<style>
</style>
