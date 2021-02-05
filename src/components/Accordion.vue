<template>
  <div class="accordion">
    <div
      class="name"
      @click="toggleAccordion"
    >
      click me
    </div>
    <div
      ref="container"
      class="container"
    >
      <div
        ref="content"
        class="content"
      >
        Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
      </div>
    </div>
  </div>
</template>

<script>
import gsap from 'gsap'

export default {
  props: {
    defaultOpen: {
      type: Boolean,
      required: false,
      default: true
    }
  },
  data () {
    return {
      isOpen: this.defaultOpen
    }
  },
  methods: {
    toggleAccordion() {
      this.isOpen = !this.isOpen
    }
  },
  watch: {
    isOpen (open) {
      if (open) {
        gsap.to(
          this.$refs.container,
          {
            height: this.$refs.content.getBoundingClientRect().height,
            clearProps: 'height'
          }
        )
      } else {
        gsap.to(
          this.$refs.container,
          { height: 0 }
        )
      }
    }
  }
}
</script>

<style scoped>
.accordion {
  width: 300px;
}

.container {
  overflow: hidden;
}
</style>
