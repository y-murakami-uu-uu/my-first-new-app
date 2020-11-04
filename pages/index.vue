<template>
  <div class="container">
    <index class="item"></index>
    <index class="item"></index>
  </div>
</template>

<script>
import index from '../components/index.vue';

export default {
  components: {
    index
  }
}

</script>

<style>
.container {
  display: flex;
}

.item {
  background: #ddd;
  margin: 10px;
  padding: 10px;
}
</style>

