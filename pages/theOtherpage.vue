<template>
  <div>
    <TransitionGroupStaggered>
      <BaseCard v-for="item in items" :key="item">
        Hello world {{ item }}
      </BaseCard>
    </TransitionGroupStaggered>
    <button @click="$router.push({ name: 'theOtherpage' })">
      Go to the index
    </button>
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
