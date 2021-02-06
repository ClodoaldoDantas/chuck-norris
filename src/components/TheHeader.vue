<template>
  <header class="header">
    <div class="container">
      <h1 class="header__title">💣 Chuck Norris</h1>
      <p class="header__description">
        Random phrases about chuck norris
      </p>
    </div>
  </header>
</template>

<script>
export default {
  name: "TheHeader"
};
</script>

<style lang="scss" scoped>
.header {
  padding: 1.5rem 0;

  &__title {
    font-size: 3.2rem;
    font-weight: bold;
  }

  &__description {
    margin-top: 0.4rem;
  }
}
</style>
