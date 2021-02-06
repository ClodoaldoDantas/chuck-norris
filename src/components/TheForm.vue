<template>
  <form @submit.prevent="handleSubmit()" class="form container">
    <select v-model="category" class="form__select">
      <option value="" disabled>Choose a category</option>

      <option
        v-for="(category, index) in categories"
        :key="index"
        :value="category"
      >
        {{ category }}
      </option>
    </select>

    <button type="submit" class="form__button" :disabled="!category">
      Random
    </button>
  </form>
</template>

<script>
import { onMounted, ref } from "vue";

export default {
  name: "TheForm",
  setup(props, context) {
    const category = ref("");
    const categories = ref([]);

    const fetchCategories = async () => {
      const url = "https://api.chucknorris.io/jokes/categories";
      const response = await fetch(url);

      categories.value = await response.json();
    };

    const handleSubmit = () => {
      context.emit("update", category.value);
    };

    onMounted(() => {
      fetchCategories();
    });

    return {
      category,
      categories,
      handleSubmit
    };
  }
};
</script>

<style lang="scss" scoped>
.form {
  display: flex;

  &__select {
    padding: 1rem;
    border: 1px solid #bbb;
    background-color: #fff;
    flex: 1;

    border-top-left-radius: 0.5rem;
    border-bottom-left-radius: 0.5rem;
  }

  &__button {
    min-width: 10rem;
    background-color: var(--primary);
    font-weight: bold;
    color: #fff;
    border: 0;

    border-top-right-radius: 0.5rem;
    border-bottom-right-radius: 0.5rem;

    &:disabled {
      opacity: 0.8;
      cursor: not-allowed;
    }
  }
}
</style>
