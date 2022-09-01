<template>
  <div id="app">
    <AppAccordion />
  </div>
</template>

<script>
import tabData from "@/assets/data.json";
import AppAccordion from "@/components/AppAccordion/AppAccordion.vue";

export default {
  name: "App",
  components: {
    AppAccordion,
  },
  data() {
    return {
      tabData: tabData,
    };
  },
  provide() {
    return { tabData: this.tabData };
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: var(--color-text);
  margin-top: 60px;
}
</style>
