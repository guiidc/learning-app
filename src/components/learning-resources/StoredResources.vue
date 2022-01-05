<template>
    <ul v-for="res in resources" :key="res.id">
    <learning-resources
      :title="res.title"
      :link="res.link"
      :description="res.description"
    />
  </ul>
</template>

<script>
import LearningResources from './LearningResources.vue'
export default {
  components: { LearningResources },
  inject: ['resources'],
}
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>