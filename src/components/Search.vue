<template>
  <div class="search">
    <div class="search__title">{{ title }}</div>
    <div>
      <input
        class="search__field"
        type="text"
        :placeholder="placeholder"
        @input="updateValue($event.target.value)"
        v-model="searchInput"
      />
    </div>
  </div>
</template>

<script>
import { mapActions } from 'vuex';

export default {
  name: 'Search',
  props: {
    placeholder: {
      type: String,
      default: 'Введите Id или имя',
    },
    title: {
      type: String,
      default: 'Поиск сотрудников',
    },
  },
  data() {
    return {
      searchInput: ''
    }
  },
  methods: {
    ...mapActions(['setTextField']),

     updateValue(value) {
      const delayMs = 700;

      if (this.timer) {
        clearTimeout(this.timer);
      }

      this.timer = setTimeout(() => {
        this.setTextField(Boolean(value));
        this.$emit('updateValue', value);

        if (value) {
          this.getUsers(value);
        }
      }, delayMs);
    },
  },
};
</script>

<style lang="scss" scoped>
  @import '@/assets/scss/search.scss';
</style>
