<template>
  <section>Filter</section>
  <section>
    <div class="controls">
      <button>Refresh</button>
      <router-link to="/register">Register as Coach</router-link>
    </div>
    <ul v-if="hasCoaches">
      <coache-item
        v-for="coach in filteredCoaches"
        :key="coach.id"
        :id="coach.id"
        :first-Name="coach.firstName"
        :last-Name="coach.lastName"
        :rate="coach.hourlyRate"
        :areas="coach.areas"
      ></coache-item>
    </ul>
    <h3 v-else>No coaches found.</h3>
  </section>
</template>

<script>
import CoacheItem from '../../components/coaches/CoachItem.vue';
export default {
  components: {
    CoacheItem,
  },
  computed: {
    filteredCoaches() {
      return this.$store.getters['coaches/coaches'];
    },
    hasCoaches() {
      return this.$store.getters['coaches/hasCoaches'];
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

.controls {
  display: flex;
  justify-content: space-between;
}
</style>
