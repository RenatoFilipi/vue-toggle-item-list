<template>
  <div class="content">
    <ul>
      <li v-for="user in users" :key="user.id">
        <div
          v-if="!user.showDetails"
          @click="user.showDetails = !user.showDetails"
        >
          <div class="simple">
            <p>{{ user.username }}</p>
          </div>
        </div>
        <div
          v-if="user.showDetails"
          @click="user.showDetails = !user.showDetails"
        >
          <div class="detail">
            <p>{{ user.name }}</p>
            <p>{{ user.email }}</p>
            <p>{{ user.phone }}</p>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "index",

  data() {
    return {
      response: {},
      users: [],
    };
  },

  methods: {
    show(user) {
      user.showDetails = true;
    },

    hide(user) {
      user.showDetails = false;
    },

    async fetchData() {
      const response = await fetch(
        "https://jsonplaceholder.typicode.com/users"
      );

      this.response = await response.json();

      this.response.forEach((item) => {
        this.users.push({ ...item, showDetails: false });
      });
    },
  },

  mounted() {
    this.fetchData();
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

ul {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

li {
  gap: 1rem;
  cursor: pointer;
}

.simple {
  display: flex;
}

.details {
  display: flex;
  gap: 1rem;
}
</style>
