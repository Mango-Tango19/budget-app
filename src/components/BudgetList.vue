<template>
  <div class="budget-list-wrap">
    <el-card :header="header">
      <template v-if="!isEmpty">
        <div class="list-item" v-for="(item, prop) in list" :key="prop">
          <span class="budget-comment">{{ item.comments }}</span>
          <span class="budget-value">{{ item.value }}</span>
          <el-button type="danger" size="mini">delete</el-button>
        </div>
      </template>
      <el-alert v-else :title="title" type="info" :closable="false"> </el-alert>
    </el-card>
  </div>
</template>

<script>
export default {
  name: "BudgetList",
  props: {
    list: {
      type: Object,
      default: () => ({}),
    },
  },
  data: () => ({
    header: "Budget List",
    title: "Empty List",
  }),
  computed: {
     isEmpty() {
      return !Object.keys(this.list).length 
  }
}
}
</script>

<style scooped>
.budget-list-wrap {
  max-width: 500px;
  margin: auto;
}

.list-item {
  display: flex;
  align-items: center;
  padding: 10px 15px;
  justify-content: center;
}

.budget-value {
  font-weight: bold;
  margin-left: auto;
  margin-right: 20px;
}
</style>