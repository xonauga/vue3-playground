<template>
  <div>Vue Learning Content</div>
  <div class="learning-content-container">
    <div>components</div>
    <div>props</div>
    <div>v-for</div>
    <div>v-text</div>
    <div>interpolation</div>
    <div>computed</div>
  </div>
  <div class="learning-content-container">
    <div>watcher</div>
    <div>v-bind</div>
    <div>v-model</div>
    <div>v-on</div>
    <div>methods</div>
  </div>
  <div class="learning-content-container">
    <div>communication</div>
    <div>v-if-else</div>
    <div>v-show</div>
    <div>refs</div>
  </div>
</template>

<script>
export default {
  name: 'LearningContent',
};
</script>

<style scoped>
.learning-content-container {
  display: flex;
  justify-content: center;
  width: 60%;
  margin: auto;
}

.learning-content-container div {
  flex: 1;
  background-color: rgb(88, 171, 140);
  margin: 5px;
  padding: 5px;
  border-radius: 5px;
  font-size: 0.8em;
  color: white;
}
</style>
>
