<template>
  <div class="container">
    <blockquote v-if="!loading" class="phrase">
      <img :src="data.icon_url" alt="Icon chuck norris" />
      <p>{{ data.value }}</p>
    </blockquote>

    <p v-else>loading phrase ...</p>
  </div>
</template>

<script>
export default {
  name: "Phrase",
  props: {
    data: {
      type: Object,
      required: true
    },
    loading: {
      type: Boolean,
      required: true
    }
  }
};
</script>

<style lang="scss" scoped>
.container {
  margin-top: 3rem;
}

.phrase {
  padding: 1rem;
  background: #ededed;
  font-style: italic;
  border-left: 0.5rem solid var(--primary);

  display: flex;
  align-items: center;

  img {
    width: 5rem;
    margin-right: 1rem;
  }
}
</style>
