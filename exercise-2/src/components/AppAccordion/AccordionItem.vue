<script>
export default {
  props: {},
  inject: ["accordionContext"],
  data() {
    return {
      index: null,
    };
  },
  computed: {
    isVisible() {
      return this.index == this.accordionContext.activeIndex;
    },
  },
  methods: {
    open() {
      if (this.isVisible) {
        this.accordionContext.activeIndex = null;
      } else {
        this.accordionContext.activeIndex = this.index;
      }
    },
    start(el) {
      el.style.height = el.scrollHeight + "px";
    },
    end(el) {
      el.style.height = "";
    },
  },
  created() {
    this.index = this.accordionContext.count++;
  },
};
</script>

<template>
  <div class="accordion__item">
    <div
      class="accordion__trigger"
      :class="{ accordion__trigger_active: isVisible }"
      @click="open"
    >
      <slot name="accordion-header"></slot>
      <span class="icon" :class="{ icon_active: isVisible }"></span>
    </div>
  </div>
  <transition
    name="accordion"
    @enter="start"
    @after-enter="end"
    @before-leave="start"
    @after-leave="end"
  >
    <div class="accordion__content" v-show="isVisible">
      <slot name="accordion-content"></slot>
    </div>
  </transition>
</template>

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

  &__item {
    cursor: pointer;
    border-bottom: 1px solid var(--color-border);
    position: relative;
    color: var(--color-text);

    @include md {
      order: 0;
    }
  }

  &__trigger {
    display: flex;
    justify-content: space-between;

    @include md {
      padding: 0 20px;
    }

    &_active {
      @include md {
        border-bottom: 1px solid var(--color-border-dark);
      }
    }

    .icon {
      $size: 8px;
      display: block;
      position: absolute;
      top: 0;
      right: 1.25rem;
      bottom: 0;
      margin: auto;
      width: $size;
      height: $size;
      border-right: 2px solid var(--color-text);
      border-bottom: 2px solid var(--color-text);
      transform: translateY(-$size / 4) rotate(45deg);
      transition: transform 0.5s ease;

      @include md {
        display: none;
      }

      &.icon_active {
        transform: translateY($size / 4) rotate(225deg);
      }
    }
  }

  &__content {
    width: 100%;

    @include md {
      order: 1;
    }
  }
}

.accordion-enter-active,
.accordion-leave-active {
  will-change: height, opacity;
  transition: height 0.5s ease, opacity 0.5s ease;
  overflow: hidden;
}

.accordion-enter,
.accordion-leave-to {
  height: 0 !important;
  opacity: 0;
}
</style>
