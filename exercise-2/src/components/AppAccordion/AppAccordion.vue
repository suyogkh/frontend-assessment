<template>
  <div class="accordion">
    <AccordionItem v-for="item in tabData" :key="item.title">
      <template #accordion-header>
        <h3>{{ item.title }}</h3>
      </template>
      <template #accordion-content>
        <div v-html="item.content"></div>
      </template>
    </AccordionItem>
  </div>
</template>

<script>
import AccordionItem from "@/components/AppAccordion/AccordionItem.vue";

export default {
  components: {
    AccordionItem,
  },
  props: {},
  inject: ["tabData"],

  data() {
    return {
      accordionContext: {
        count: 0,
        activeIndex: 0,
      },
    };
  },
  provide() {
    return { accordionContext: this.accordionContext };
  },
};
</script>

<style lang="scss" scoped>
$screen-md-min: 768px;
@mixin md {
  @media (min-width: #{$screen-md-min}) {
    @content;
  }
}

.accordion {
  @include md {
    display: flex;
    flex-wrap: wrap;
  }

  &__item:last-child {
    border-bottom: none;
  }
}
</style>
