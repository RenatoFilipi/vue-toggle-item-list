<template>
  <div class="content">
    <div class="list">
      <item-2 v-for="(user, index) in dynamicList" :key="index" :user="user" />
    </div>
  </div>
</template>
<script>
import item2 from "~/components/item2.vue";
export default {
  name: "example2",
  components: {
    item2,
  },

  data() {
    return {
      dynamicList: [],
    };
  },

  methods: {
    async fetchData() {
      let list = [
        { name: "ola", age: 16 },
        { name: "sam", age: 18 },
        { name: "lop", age: 45 },
      ];

      list.forEach((item) => {
        this.dynamicList.push({ ...item, visible: false });
      });
    },
  },

  async created() {
    await this.fetchData();
  },
};
</script>
<style lang="css" scoped>
.content {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.list {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
</style>
