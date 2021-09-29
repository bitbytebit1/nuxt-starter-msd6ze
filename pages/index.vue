<template>
  <div>
    <AppNavbar />
    <TransitionGroupStaggered>
      <BaseCard v-for="item in items" :key="item">
        These components stagger2 just fine {{ item }}
      </BaseCard>
    </TransitionGroupStaggered>
    <button @click="$router.push({ name: 'theOtherpage' })">
      Go to the the other page
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: ['1', '2', '3'],
    };
  },
};
</script>
