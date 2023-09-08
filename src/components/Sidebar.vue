<template>
  <div class="sidebar">
    <Search 
      class="sidebar__search"
      @updateValue="getUsers"
    ></Search>
    <Results></Results>
  </div>
</template>

<script>
import { mapActions } from 'vuex';
import Search from '@/components/Search';
import Results from '@/components/results/Results';

export default {
  name: 'Sidebar',
  components: {
    Search,
    Results,
  },
  methods: {
    ...mapActions(['getUsers']),
  },
};
</script>

<style lang="scss" scoped>
  @import '@/assets/scss/sidebar.scss';
</style>
