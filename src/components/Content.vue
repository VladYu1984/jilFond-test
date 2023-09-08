<template>
  <div class="content">
    <img
      class="content__image"
      v-if="currentUser?.id"
      src="@/assets/images/image_big.svg"
      alt=""
    />
    <div class="content__text" v-if="currentUser?.id">
      <div class="content__title">{{ currentUser?.name }}</div>
      <div class="content__email">
        <span class="content__email--bold">email: </span
        >{{ currentUser?.email }}
      </div>
      <div class="content__phone">
        <span class="content__phone--bold">phone: </span
        >{{ currentUser?.phone }}
      </div>
      <div class="content__about">О себе:</div>
      <div class="content__about-text">
        {{ currentUser.company?.catchPhrase }}
      </div>
    </div>
    <div class="content__stub" v-if="!currentUser.id">
      Выберите сотрудника, чтобы посмотреть его профиль
    </div>
  </div>
</template>

<script>
import { mapState } from 'vuex';

export default {
  computed: {
    ...mapState(['currentUser']),
  },
};
</script>

<style lang="scss">
  @import '@/assets/scss/content.scss';
</style>
