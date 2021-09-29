<template>
  <div
    class="appNavbar__item c-pointer"
    :class="{
      'appNavbar__item--active': $route.name === item.routeName,
    }"
  >
    {{ item.text }}
  </div>
</template>

<script>
export default {
  props: {
    item: { type: Object, default: () => ({}) },
  },
};
</script>

<style>
.appNavbar__item--active {
  background: rgba(255, 255, 255, 0.3);
}

.appNavbar__item:hover:not(.appNavbar__item--active) {
  background-color: rgba(255, 255, 255, 0.1);
}

.appNavbar__item {
  padding: 1.2rem;
}
.appNavbar__item:hover {
  text-shadow: 0.3px -0.1px 0.1px rgb(255, 0, 0),
    0.2px 0.1px 0.1px rgb(0, 255, 0), -0.1px 0.2px 0.1px rgb(0, 0, 255);
}
</style>
