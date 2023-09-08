<template>
  <div class="results">
    <div class="results__title">Результаты</div>
    <div class="results__total" v-if="!users.length && !textField">
      Начните поиск
    </div>
    <div class="results__total" v-if="!users.length && textField">
      Ничего не найдено
    </div>
    <ResultsItem
      v-for="user in users"
      :key="user.id"
      :user="user"
      class="results__item"
      @click.native="setUser(user)"
    >
    </ResultsItem>
  </div>
</template>

<script>
import { mapState, mapActions } from 'vuex';
import ResultsItem from '@/components/results/ResultsItem';

export default {
  name: 'Results',
  components: {
    ResultsItem,
  },
  computed: {
    ...mapState(['users', 'textField']),
  },
  methods: {
    ...mapActions(['setUser']),

    setCurrentUser(user) {
      this.setUser(user);
    },
  },
};
</script>

<style lang="scss" scoped>
  @import '@/assets/scss/results.scss';
</style>
