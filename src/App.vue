<template>
  <section id="header">
    <div class="header">
      <img class="vue-logo" alt="Vue logo" src="./assets/logo.png" />
      <div class="h3">Willkommen zum Vue Tutorial</div>
      <hr>
    </div>
  </section>
  <section id="main">
    <div class="main">
      <section id="first_lesson">
        <div class="h5">First Lesson: HTML Tabelle</div>
        <learning-content />
        <hr>
        <materials-table />
      </section>
    </div>
  </section>
</template>

<script>
import MaterialsTable from './components/MaterialsTable.vue';
import LearningContent from './components/LearningContent.vue';

export default {
  name: 'App',
  components: {
    MaterialsTable,
    LearningContent,
  },
};
</script>

<style>
body {
  background-color: #455e87;
  font-family: 'Montserrat', sans-serif;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #3fb883;
  margin-top: 20px;
}

hr {
  height: 1px;
  background-color: #6884b1 !important;
  opacity: 1;
}

.header {
  text-align: center;
}

.main {
  margin-top: 10px;
  text-align: center;
}

.vue-logo {
  width: 80px;
  animation: vue-logo 6s infinite linear;
  text-align: center;
}

@keyframes vue-logo1 {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(359deg);
  }
}
</style>
