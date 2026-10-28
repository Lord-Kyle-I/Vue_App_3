<script>
  import Sort from "@/components/Sort.vue";

  export default {
    name: 'SortList',
    components: {
      Sort,
    },
    methods: {
      changeSort(name, sortWay) {
        const target = this.$refs.sorts.find(s => s.name === name)
        this.$refs.sorts.forEach(s => {
          if(s !== target) {
            s.reset()
          }
        })
        target.filterClick()
        if(target.clicks !== 0) {
          this.$emit('sort', sortWay)
        } else {
          this.$emit('sort', null)
        }
      }
    },
    props: {
      sorts: {type: Array, required: true},
    },
  }
</script>

<template>
  <sort ref="sorts" v-for="sort in sorts" :sort-type="sort.sortType" :name="sort.name" :key="sort.name"
        :class="sort.customClasses" @on-click="changeSort" :property="sort.property"></sort>
</template>

<style scoped>

</style>