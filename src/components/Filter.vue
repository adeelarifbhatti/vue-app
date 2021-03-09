<template>
      <button class="btn btn__nav" @click="updateFilter('all')"
      :class="{active: current ==='all'}">

          View All
      </button>
        <button class="btn btn__nav" @click="updateFilter('completed')"
              :class="{active: current ==='completed'}">
          Completed
      </button>
        <button class="btn btn__nav" @click="updateFilter('incompleted')"
              :class="{active: current ==='incompleted'}">
          Incompleted
      </button>

</template>

<script>
export default {
    props: ['current'],
    methods: {
        updateFilter(by) {
            this.$emit('filterChange',by);
        }
    }
}
</script>

<style>

</style>