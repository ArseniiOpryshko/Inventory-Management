<template>
  <div>
    <div class="films-grid__film" @click="openFilm(film.id)">
      <img class="films-grid__img" :src="film.filmImage" alt="Film image" />
      <div class="films-grid__desc">
        <h3 class="desc__name">{{ film.name }}</h3>
        <p class="desc__text">
          {{ formatDate(film.publishDate) }}
        </p>
      </div>
    </div>
  </div>
</template>

<script setup>
const { film } = defineProps(["film"]);
const router = useRouter();

function openFilm(filmId) {
  router.push("/" + filmId);
}
function formatDate(dateString) {
  const options = { day: "2-digit", month: "long", year: "numeric" };
  return new Date(dateString).toLocaleDateString("en-US", options);
}
</script>
