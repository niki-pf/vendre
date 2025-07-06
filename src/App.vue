<template>
  <main>
    <AppHero />
    <div class="container">
      <h1>Våra anställda</h1>

      <div class="grid">
        <EmployeeCard
          v-for="employee in users"
          :key="employee.id"
          :name="employee.firstName + ' ' + employee.lastName"
          :email="employee.email"
          :image="employee.image"
          :phone="employee.phone"
          :city="employee.address.city"
          :company="employee.company.name"
          :title="employee.company.title"
        />
      </div>

      <div class="pagination">
        <button :disabled="page === 1" @click="prevPage">Föregående</button>
        <button @click="nextPage">Nästa</button>
      </div>
    </div>
  </main>
</template>

<script>
import EmployeeCard from "./components/EmployeeCard.vue";
import AppHero from "./components/AppHero.vue";
export default {
  components: {
    EmployeeCard,
    AppHero,
  },
  data() {
    return {
      users: [],
      page: 1,
      limit: 8,
    };
  },
  methods: {
    async fetchUsers() {
      const skip = (this.page - 1) * this.limit;
      const res = await fetch(
        `https://dummyjson.com/users?limit=${this.limit}&skip=${skip}`
      );
      const data = await res.json();
      this.users = data.users;
    },
    nextPage() {
      this.page++;
      this.fetchUsers();
    },
    prevPage() {
      if (this.page > 1) {
        this.page--;
        this.fetchUsers();
      }
    },
  },
  mounted() {
    this.fetchUsers();
  },
};
</script>

<style>
html,
body {
  max-width: 100%;
  overflow-x: hidden;
}
body {
  font-family: "Segoe UI", sans-serif;
  background-color: #eeebfc;
  margin: 0;
}

.container {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  max-width: 1200px;
  overflow: hidden;
  margin: auto;
  padding: 0 1rem;
}
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 1.5rem;
  justify-content: start;
  padding: 0 1rem;
}
@media (max-width: 600px) {
  .grid {
    grid-template-columns: 1fr;
    padding: 0 0.5rem;
    row-gap: 1rem;
    column-gap: 0;
  }
}

.pagination {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin: 2rem auto 2rem;
  flex-wrap: wrap;
}
button {
  padding: 0.5rem 1rem;
  background-color: #5333ed;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}
button:disabled {
  background-color: #ccc;
  cursor: not-allowed;
}
h1 {
  text-align: center;
}

.card h3 {
  text-align: center;
}
</style>
