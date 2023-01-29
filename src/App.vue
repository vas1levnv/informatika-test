<template>
  <div class="app-wrapper">
    <header-page></header-page>
    <main-page></main-page>
  </div>
</template>
<script>


import MainPage from "@/components/main-page.vue";
import HeaderPage from "@/components/header-page.vue";

export default {
  components: {HeaderPage, MainPage}

};
</script>

<style>

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

a {
  color: inherit;
  text-decoration: none;
  transition:  all 0.3s ease;
}

ul {
  list-style-type: none;
}

.app-wrapper {
  font-family: Arial;
  color: white;
  min-height: 100vh;
  min-width: 320px;
  width: 100vw;
  background: rgb(2, 0, 36);
  background: radial-gradient(circle, rgba(2, 0, 36, 1) 0%, rgba(77, 82, 130, 1) 0%, rgba(2, 9, 35, 1) 71%);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}


.container {
  max-width: 1200px;
  padding: 0 30px;
  margin: 0 auto;
}

</style>