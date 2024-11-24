<template>
  <section class="films-section">
    <h2 class="films-section__title">Our collection</h2>
    <div class="films-grid">
      <!-- <div v-if="!films">Loading...</div> -->
      <Film v-for="film in data" :key="film.id" :film="film" />
      <!-- {{ data }} -->
    </div>
  </section>
</template>

<script setup>
const { data } = await useFetch("http://localhost:3000/films");
</script>

<style>
.films-section {
  width: 100%;
}
.films-section__title {
  font-size: 35px;
  margin: 20px 0;
  text-align: center;
}
.films-grid {
  width: 100%;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 20px;
}
.films-grid__film {
  display: flex;
  flex-direction: column;
  width: 320px;
  position: relative;
  gap: 10px;
  cursor: pointer;
}
.films-grid__img {
  /* width: 100%;  */
  /* height: 90%;  */
  object-fit: cover;
  border-radius: 2px;
}
.films-grid__desc {
  font-weight: bold;
}
.desc__name {
}
.desc__text {
  color: rgb(191, 191, 191);
}
</style>
