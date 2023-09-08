<template>
  <div class="results-item" :class="objectStyle">
    <img
      class="results-item__image"
      src="@/assets/images/image_small.svg"
      alt=""
    />
    <div class="results-item__wrapper">
      <div class="results-item__title">{{ user.username }}</div>
      <div class="results-item__email">{{ user.email }}</div>
    </div>
  </div>
</template>

<script>
import { mapActions, mapState } from 'vuex';

export default {
  name: 'ResultsItem',
  props: {
    content: {
      type: Object,
      default() {
        return {};
      },
    },
    user: {
      type: Object,
      default() {
        return {};
      },
    },
    active: {
      type: Boolean,
      default: false,
    },
  },
  computed: {
    ...mapState(['currentUser']),
    objectStyle() {
      return {
        'results-item--active': this.currentUser.id === this.user.id,
      };
    },
  },
  methods: {
    ...mapActions(['setUser']),
  },
};
</script>

<style lang="scss" scoped>
  @import '@/assets/scss/results.scss';
</style>
