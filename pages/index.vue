<template>
  <div>
    <TransitionGroupStaggered>
      <BaseCard v-for="item in items" :key="item">
        These components stagger just fine {{ item }}
      </BaseCard>
    </TransitionGroupStaggered>
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
