<template>
  <TheHeader />
  <TheForm @update="getRandomPhraseByCategory" />
  <Phrase :loading="loading" :data="phrase" />
</template>

<script>
import { onMounted, ref } from "vue";
import TheHeader from "@/components/TheHeader";
import TheForm from "@/components/TheForm";
import Phrase from "@/components/Phrase";

export default {
  name: "App",
  components: {
    TheHeader,
    TheForm,
    Phrase
  },
  setup() {
    const phrase = ref({});
    const loading = ref(false);

    const getRandomPhraseByCategory = async category => {
      loading.value = true;
      const url = `https://api.chucknorris.io/jokes/random?category=${category}`;
      const response = await fetch(url);

      phrase.value = await response.json();
      loading.value = false;
    };

    const getRandomPhrase = async () => {
      loading.value = true;
      const url = "https://api.chucknorris.io/jokes/random";
      const response = await fetch(url);

      phrase.value = await response.json();
      loading.value = false;
    };

    onMounted(() => {
      getRandomPhrase();
    });

    return {
      phrase,
      loading,
      getRandomPhraseByCategory
    };
  }
};
</script>

<style lang="scss">
@import url("./assets/scss/global.scss");
</style>
