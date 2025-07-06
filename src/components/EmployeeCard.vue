<template>
  <article class="card">
    <img :src="image" alt="Profilbild" />
    <h3>{{ name }}</h3>
    <a class="email" :href="`mailto:${email}`">{{ email }}</a>
    <p><strong>Telefon:</strong> {{ phone }}</p>
    <p><strong>Stad:</strong> {{ city }}</p>
    <p><strong>Företag:</strong> {{ company }}</p>
    <p><strong>Roll:</strong> {{ title }}</p>
  </article>
</template>

<script>
export default {
  name: "EmployeeCard",
  props: {
    name: String,
    email: String,
    image: String,
    phone: String,
    city: String,
    company: String,
    title: String,
  },
};
</script>

<style scoped>
.card {
  background: white;
  padding: 1rem;
  border-radius: 8px;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);
  box-sizing: border-box;
  max-width: 100%;
}
@media (max-width: 600px) {
  .card {
    width: 80%;
    margin: auto;
  }
}
.card img {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  object-fit: cover;
  margin: 0 auto 1rem auto;
  display: block;
}
h2 {
  margin: 0;
  font-size: 1.2rem;
}
a {
  color: #0077cc;
  text-decoration: none;
}

img,
h2 {
  justify-content: center;
}

.email {
  word-break: break-word;
}

.card p {
  margin: 0.3rem 0;
  line-height: 1.4;
  color: #444;
}
</style>
