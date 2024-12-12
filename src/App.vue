<template>
  <div>

    <Header />

    <nav>
      <Tabs :currentTab="currentTab" @update-tab="changeTab" />
    </nav>

    <main>
      <div class="cards-container">
        <section v-if="currentTab === 'Standings'">
          <Card v-for="team in standings" :key="team._id" :data="team" />
        </section>
        <section v-if="currentTab === 'Players'">
          <Card v-for="player in players" :key="player._id" :data="player" />
        </section>
        <section v-if="currentTab === 'Matches'">
          <Card v-for="match in matches" :key="match._id" :data="match" />
        </section>
      </div>

    </main>

    <AppFooter @update-tab="changeTab" />

  </div>
</template>

<script>
import Tabs from './components/DataTabs.vue';
import Card from './components/GenericCard.vue';
import Header from './components/AppHeader.vue'; 
import AppFooter from './components/AppFooter.vue';

export default {
  components: { Tabs, Card, Header, AppFooter },
  data() {
    return {
      currentTab: 'Standings',
      standings: [],
      players: [],
      matches: []
    };
  },
  methods: {
    async changeTab(tab) {
      this.currentTab = tab;
      this.fetchData(tab);
    },
    async fetchData(tab) {
      try {
        const baseURL = process.env.VUE_APP_BASE_URL;
        let response;
        if (tab === 'Standings') {
          response = await fetch(`${baseURL}/standings`);
          this.standings = await response.json();
        } else if (tab === 'Players') {
          response = await fetch(`${baseURL}/players`);
          this.players = await response.json();
        } else if (tab === 'Matches') {
          response = await fetch(`${baseURL}/matches`);
          this.matches = await response.json();
        }
      } catch (error) {
        console.error('Error fetching data:', error);
      }
    }
  },
  mounted() {
    this.fetchData('Standings');
  }
};
</script>