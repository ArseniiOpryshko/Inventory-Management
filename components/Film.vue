<template>
  <div class="films-grid__film">
    <img class="films-grid__img" :src="film.filmImage" alt="Film image" />
    <div class="films-grid__desc">
      <h3 class="desc__name">{{ film.name }}</h3>
      <p class="desc__text">
        {{ film.publishDate }}
      </p>
    </div>
  </div>
</template>

<script setup>
defineProps({
  film: {
    type: Object,
    required: true,
  },
});
</script>
