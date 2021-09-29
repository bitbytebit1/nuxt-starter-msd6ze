<template>
  <nav
    class="appNavbar"
    :class="{
      'appNavbar--open': isNavbarVisible,
      'appNavbar--closed': !isNavbarVisible,
    }"
    @click="isNavbarVisible = !isNavbarVisible"
  >
    <!-- Items -->

    <TransitionGroupStaggered
      class="appNavbar__items"
      :delay="500"
      name="slide-x"
      :stagger="2000"
      @click="toggleNavbar"
    >
      <AppNavbarItem
        v-for="item in isNavbarVisible ? navbarItems : []"
        :key="item.routeName"
        :item="item"
        @click.stop.native="pushRoute(item)"
      />
    </TransitionGroupStaggered>
    <!-- Button -->
    <div
      v-if="!isNavbarVisible"
      key="button"
      class="appNavbar__activator pa-10 c-pointer"
      @click.stop="toggleNavbar"
    >
      <BaseIcon class="fs-38"> list </BaseIcon>
    </div>
  </nav>
</template>
<script>
export default {
  data() {
    return {
      isNavbarVisible: false,
      transitionKey: Math.random(),
      navbarItems: this.getData(),
    };
  },
  mounted() {},
  methods: {
    toggleNavbar() {
      this.transitionKey = Math.random();
      this.isNavbarVisible = !this.isNavbarVisible;
    },
    getData() {
      return this.$router.options.routes
        .map((route) => {
          const routeName = route.name;
          const upperCase = routeName[0].toUpperCase() + routeName.slice(1);
          return { text: upperCase, name: route.name, routeName };
        })
        .sort((a, b) => a.text.localeCompare(b.text));
    },
    pushRoute(route) {
      this.$router.push(this.localePath(route.routeName));
      this.isNavbarVisible = false;
    },
  },
};
</script>

<style>
.flip-list-move {
  transition: transform 1s;
}
.appNavbar__items {
  position: relative;
  z-index: 100;
}
.appNavbar {
  color: var(--text-color-brand);
  width: 100%;
  height: 0;
  z-index: 10;
}
.appNavbar--open {
  height: 100%;
}
.appNavbar::before {
  content: '';
  display: block;
  position: absolute;
  background: #7d8529;
  top: 0;
  right: 0;
  width: 0%;
  height: 5%;
  border-radius: 0 0 0 80px;
  transition: all 0.3s cubic-bezier(0.33333, 0.66667, 0.66667, 1);
}
.appNavbar--open::before {
  width: 121%;
  height: 100%;
}
.appNavbar__activator {
  position: absolute;
  right: 0;
}
</style>
