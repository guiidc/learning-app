<template>
  <ul v-for="res in storedResources" :key="res.id">
    <learning-resources :title="res.title" :link="res.link" :description="res.description"/>
  </ul>
</template>

<script>
import LearningResources from './components/learning-resources/LearningResources.vue';
export default {
  components: { LearningResources },
  data() {
    return {
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The VueJS documentation',
          link: 'https://vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Search with google',
          link: 'https://google.com',
        },
      ]
    }
  },
}
</script>