<template>
  <div class="item">
    <button @click="user.visible = !user.visible">show</button>
    <div v-show="!user.visible">{{ user.name }}</div>
    <div v-show="user.visible">
      this is {{ user.name }}, {{ user.age }} years old
    </div>
  </div>
</template>
<script>
export default {
  name: "item2",

  props: {
    user: Object,
  },

  data() {
    return {
      show: false,
    };
  },
};
</script>
<style lang="css">
.item {
  display: flex;
  gap: 1rem;
}
</style>
