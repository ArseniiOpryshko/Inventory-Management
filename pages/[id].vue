<template>
  <div>
    <Navbar v-model="sharedData" />
    <SpecificFilm :data="sharedData" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      sharedData: "",
    };
  },
  watch: {
    sharedData(newValue) {
      console.log("sharedData updated:", newValue);
    },
  },
};
</script>
