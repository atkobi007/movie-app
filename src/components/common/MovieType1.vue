<script setup>
import MovieTitle from './MovieTitle.vue'
import MovieItem from './MovieItem.vue'

const props = defineProps({
  list: Array,
  title: String,
})

const getData = computed(() => {
  return props.list ?? []
})
</script>

<template>
  <div class="item-root">
    <MovieTitle title="HOT" title-color="white" />
    <MovieItem v-for="info in getData" :key="info" />
  </div>
</template>

<style scoped>
.item-root {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  width: 100%;
  padding-left: 8px;
  padding-right: 8px;
  padding-top: 20px;
}
</style>
