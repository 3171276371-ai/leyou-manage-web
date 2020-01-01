<template>
  <v-card>
      <v-flex xs12 sm10>
        <v-tree url="/item/category/list"
                :isEdit="isEdit"
                @handleAdd="handleAdd"
                @handleEdit="handleEdit"
                @handleDelete="handleDelete"
                @handleClick="handleClick"
        />
      </v-flex>
  </v-card>
</template>

<script>
  export default {
    name: "category",
    data() {
      return {
        isEdit:true
      }
    },
    methods: {
      handleAdd(node) {
        console.log("add .... ");
        console.log(node);
      },
      handleEdit(id, name) {
        console.log("edit... id: " + id + ", name: " + name)
      },
      handleDelete(id) {
          // this.$message.confirm("确认要删除分组吗？")
          // .then(() => {
            this.$http.delete("/item/category/delete/" + id)
                .then(() => {
                    this.$message.success("删除成功");
                    this.loadData();
                })
          // })
      },
      handleClick(node) {
        console.log(node)
      }
    }
  };
</script>

<style scoped>

</style>
