<template>
  <section class="films-section">
    <h2 class="films-section__title">Our collection</h2>
    <div v-if="filteredFilms.length > 0" class="films-grid">
      <Film v-for="film in filteredFilms" :key="film.id" :film="film" />
    </div>
    <div v-else>
      <p>No films found.</p>
    </div>
  </section>
</template>
<script setup>
const props = defineProps({
  data: String,
});

const { data: filmsData } = useFetch("http://localhost:3000/films");

const searchString = ref(props.data);
const filteredFilms = computed(() => {
  if (!filmsData.value) return [];
  return filmsData.value.filter((film) =>
    film.name.toLowerCase().includes(searchString.value.toLowerCase())
  );
});

watch(
  () => props.data,
  (newValue) => {
    console.log("Data updated in Child2:", newValue);
    searchString.value = newValue;
  }
);
</script>

<style>
.films-section {
  width: 100%;
}
.films-section__title {
  font-size: 35px;
  margin: 20px 0;
  text-align: center;
  font-weight: bold;
}
.films-grid {
  margin: 0 auto 40px auto;
  width: 80%;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 40px 20px;
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
  object-fit: cover;
  border-radius: 2px;
  height: 450px;
}
.films-grid__desc {
  font-weight: bold;
}
.desc__text {
  color: rgb(191, 191, 191);
}
</style>
