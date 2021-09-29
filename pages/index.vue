<template>
  <div>
    <Navbar />
    <TransitionGroupStaggered>
      <BaseCard v-for="item in items" :key="item">
        Hello world {{ item }}
      </BaseCard>
    </TransitionGroupStaggered>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: ['1', '2'],
    };
  },
};
</script>
