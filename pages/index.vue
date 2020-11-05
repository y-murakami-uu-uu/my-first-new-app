<template>
  <div class="container">
    <index class="item"></index>
    <index class="item"></index>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component({
  components: {
    index: () => import('../components/index.vue')
  }
})
export default class IndexPage extends Vue {}
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

