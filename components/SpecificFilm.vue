<template>
  <section class="film-section">
    <img
      :src="film[0].filmImage"
      alt="Film image"
      class="film-section__image"
    />
    <div class="film-section__data">
      <h2 class="data__name">{{ film[0].name }}</h2>
      <p class="data__desc">{{ film[0].description }}</p>
      <p class="data__date">
        <b>Date:</b> {{ formatDate(film[0].publishDate) }}
      </p>
      <span class="data__rate"
        ><b>Rating:</b> {{ film[0].rating ? film[0].rating : "0" }}</span
      >
    </div>
  </section>
</template>

<script setup>
const { id } = useRoute().params;
const { data: film } = await useFetch("http://localhost:3000/films/" + id);

function formatDate(dateString) {
  const options = { day: "2-digit", month: "long", year: "numeric" };
  return new Date(dateString).toLocaleDateString("en-US", options);
}
</script>

<style scoped>
.film-section {
  width: 80%;
  display: flex;
  height: 600px;
  margin: 40px auto;
  gap: 20px;
}
.film-section__image {
  border-radius: 5px;
}
.film-section__data {
  display: flex;
  flex-direction: column;
  gap: 10px;
  font-size: 20px;
}
.data__name {
  font-size: 40px;
  font-weight: bold;
}
.data__desc {
}
</style>
