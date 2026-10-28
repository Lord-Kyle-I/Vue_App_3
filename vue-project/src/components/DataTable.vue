<script>
import SortList from "@/components/SortList.vue";

export default {
  name: "DataTable",
  components: {
    SortList,
  },
  props: {
    tableData: {type: Array, required: true},
    sorts: {type: Array, required: true},
    customClasses: {type: Array}
  },
  methods: {
    sortList(sortWay) {
      if(sortWay !== null) {
        this.$emit('update-list', sortWay)
      } else {
        this.$emit('update-list', null)
      }
    }
  },
}
</script>

<template>
  <div>
    <slot name="filters"></slot>

    <div :class="customClasses">
      <table class="table">
        <thead class="text-nowrap">
        <tr>
          <th scope="col"><span class="visually-hidden">Favorites</span></th>
          <sort-list :sorts="sorts" @sort="sortList"></sort-list>
          <th scope="col"><span class="visually-hidden">Actions</span></th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="data in tableData" :key="JSON.stringify(data)">
          <slot name="row-content" :data="data"></slot>
        </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  @use "sass:color";
  @import "@/scss/variables.scss";

  table {
    thead {
      .container-lg {
        --bs-gutter-x: 0rem;
      }
    }

    tr, td {
      border-color: map-get($colors, "accent");
    }
  }


</style>