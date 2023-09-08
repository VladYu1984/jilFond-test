<template>
  <div class="wrapper">
    <div class="loader-wrapper" :class="objectStyle">
      <div class="loader"></div>
    </div>
    <header class="header">
      <h1 class="header__logo">Жилфонд</h1>
      <p class="header__user">Пользователь</p>
    </header>
    <div class="main">
      <Sidebar></Sidebar>
      <Content></Content>
    </div>
  </div>
</template>

<script>
import Sidebar from '@/components/Sidebar';
import Content from '@/components/Content';
import { mapState } from 'vuex';

export default {
  name: 'Main',
  components: {
    Sidebar,
    Content,
  },
  computed: {
    ...mapState(['loading']),
    objectStyle() {
      return {
        'loader-wrapper--active': this.loading,
      };
    },
  },
};
</script>

<style lang="scss" scoped>
  @import '@/assets/scss/main.scss';
</style>
