<template>
  <base-card>
    <base-button @click="setSelectedTab('stored-resources')" :mode="storedResButtonMode">Stored Resources</base-button>
    <base-button @click="setSelectedTab('add-resources')" :mode="addResButtonMode">Add Resources</base-button>
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResources from './AddResources.vue';
export default {
  components: { StoredResources, AddResources },
  data() {
    return {
      selectedTab: 'stored-resources',
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
      ],
    }
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
      destroyResource: this.destroyResource,
    }
  },
  computed: {
    storedResButtonMode() {
      return this.selectedTab === 'stored-resources' ? null : 'flat'
    },
    addResButtonMode() {
      return this.selectedTab === 'add-resources' ? null : 'flat'
    },
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, description, link) {
      const newResource= { id: new Date().toISOString(), title, description, link};
      this.storedResources.unshift(newResource);
      this.selectedTab = 'stored-resources';
    },
    destroyResource(id) {
      const actualIndex = this.storedResources.findIndex((resource) => resource.id === id);
      this.storedResources.splice(actualIndex, 1);
    }
  }
}
</script>