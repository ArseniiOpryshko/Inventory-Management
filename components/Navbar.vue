<template>
  <header class="main-header">
    <nav class="main-header__navbar">
      <NuxtLink to="/" class="navbar_group">
        <img class="navbar__logo" src="/images/logo.png" alt="" />
        <p class="navbar__title">Cinema searcher</p>
      </NuxtLink>
      <form class="navbar__search-form">
        <input
          class="search-form__text-input"
          type="text"
          placeholder="Search name"
          v-model="localValue"
        />
        <input class="search-form__bttn" type="button" value="Search" />
      </form>
    </nav>
  </header>
</template>

<script>
export default {
  props: {
    modelValue: String,
  },
  computed: {
    localValue: {
      get() {
        return this.modelValue;
      },
      set(value) {
        this.$emit("update:modelValue", value);
      },
    },
  },
};
</script>

<style scoped>
.main-header {
  width: 100%;
  background-color: rgba(255, 255, 255, 0.079);
}
.main-header__navbar {
  display: flex;
  align-items: center;
  height: 60px;
  justify-content: space-evenly;
}
.navbar_group {
  display: flex;
  gap: 10px;
  align-items: center;
  text-decoration: white;
  color: white;
}
.navbar__logo {
  filter: invert(0);
  height: 45px;
}
.navbar__title {
  font-size: 30px;
}
.navbar__search-form {
  display: flex;
  gap: 10px;
  align-items: center;
}
.search-form__text-input {
  height: 40px;
  background-color: rgb(255, 255, 255);
  border: none;
  border-radius: 5px;
  outline: none;
  width: 200px;
  color: black;
  padding: 0 5px 0 5px;
  font-size: 16px;
}
.search-form__bttn {
  border: none;
  border-radius: 5px;
  outline: none;
  height: 30px;
  width: 60px;
  background-color: white;
  cursor: pointer;
  color: rgb(0, 0, 0);
}
</style>
