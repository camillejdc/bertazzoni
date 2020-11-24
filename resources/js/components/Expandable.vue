<template>
  <transition
    name="accordion"
    @before-enter="beforeEnter" @enter="enter"
    @before-leave="beforeLeave" @leave="leave"
  >
    <slot></slot>
  </transition>
</template>

<script>
export default {
  methods: {
    toggle () {
      this.show = ! this.show
    },
    // enter (el, done) {
    //   $(el).slideDown(150, done)
    // },
    // leave (el, done) {
    //   $(el).slideUp(150, done)
    // },
    beforeEnter (el) {
      el.style.height = '0'
    },
    enter (el) {
      el.style.height = el.scrollHeight + 'px'
    },
    beforeLeave (el) {
      el.style.height = el.scrollHeight + 'px'
      this.leaving = true
    },
    afterLeaving () {
      this.leaving = false
    },
    leave (el) {
      el.style.height = '0'
    },
  },
}
</script>
