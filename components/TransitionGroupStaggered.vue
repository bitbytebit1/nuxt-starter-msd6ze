<template>
  <transition-group
    tag="div"
    :name="name"
    :css="true"
    :appear="true"
    @before-enter="beforeEnter"
    @enter="enter"
    @after-leave="afterLeave"
  >
    <slot />
  </transition-group>
</template>

<script>
export default {
  props: {
    name: { type: String, default: 'slide-x' },
    // Amount in ms
    delay: { type: Number, default: 0.0 },
    // Amount in ms
    stagger: { type: Number, default: 150 },
  },
  data() {
    return {
      transitionDelay: this.delay,
    };
  },
  methods: {
    // ENTER
    beforeEnter(el) {
      el.style.transitionDelay = this.transitionDelay + 'ms';
      this.transitionDelay += this.stagger;
    },
    enter(el, done) {},
    afterEnter(el) {
      el.style.transitionDelay = '';
      this.transitionDelay -= this.stagger;
    },

    // LEAVE
    beforeLeave(el) {},
    leave(el, done) {
      this.transitionDelay -= this.stagger;
      done();
    },
    afterLeave(el) {},
  },
};
</script>

<style>
/* slide-x */
.slide-x-enter-active,
.slide-x-leave-active {
  transition: all 0.2s ease;
}
.slide-x-leave-to,
.slide-x-enter {
  transform: translateX(-30px);
  opacity: 0;
}
</style>
