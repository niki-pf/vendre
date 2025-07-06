<template>
  <section class="hero">
    <h1>Frontend + Vue + Ambition</h1>
    <p>
      Ett snabbt projekt inför praktikansökan hos Vendre –
      <br />
      inspirerat av er stil, med mycket respekt för er design.
    </p>
  </section>
</template>

<script>
export default {
  name: "AppHero",
};
</script>

<style scoped>
.hero {
  box-sizing: border-box;
  width: 100%;
  background-color: #ffffff;
  padding: 4rem 2rem;
  text-align: center;
  border-bottom: 2px solid #eee;
}
.hero h1 {
  font-size: clamp(1.8rem, 5vw, 3rem);
  margin-bottom: 1rem;
  color: #0077cc;
  font-weight: 700;
  background: linear-gradient(90deg, #4d18c0, #ef64a7, #f69546);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
.hero p {
  font-size: 1.1rem;
  color: #444;
  line-height: 1.6;
}
</style>
