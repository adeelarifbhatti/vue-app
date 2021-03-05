<template>
  <nav class="filter">
      <button class="btn-filter" @click="updateFilter('all')"
      :class="{active: current ==='all'}">

          View All
      </button>
        <button class="btn-filter" @click="updateFilter('completed')"
              :class="{active: current ==='completed'}">
          Completed
      </button>
        <button class="btn-filter" @click="updateFilter('incompleted')"
              :class="{active: current ==='incompleted'}">
          Incompleted
      </button>
  </nav>
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

.btn-filter{ 
    text-transform: uppercase;
    text-decoration: none;
    margin-bottom: .7rem;
    margin-top: .1rem;
    margin-right: .5rem;
    padding: .1rem 1rem;
    display: inline-block;
    border-radius: .5rem;
    transition: all .1s;
    background-color: rgba(209, 226, 208, 0.411);
    color: rgb(24, 22, 19);
    }
.filter button.active {
    color: rgb(149, 226, 123);
        border-radius: 0rem;
}

</style>