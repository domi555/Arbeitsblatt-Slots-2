<template>
  <div>
    <h3>Scratchy Inc.</h3>

    <h4>Boss</h4>
    <slot name="boss" :item="boss"> </slot>

    <h4 class="mt-4">Employees</h4>
    <div class="d-flex flex-row">
      <div v-for="(cat, i) of employees" :key="i" class="me-3">
        <slot name="employees" :item="cat"> </slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    cats: {
      type: Array,
    },
  },
  data() {
    return {
      boss: this.cats.find((el) => el.role == 'Boss'),
      employees: this.cats.filter((el) => el.role != 'Boss'),
    };
  },
};
</script>

<style scoped></style>
