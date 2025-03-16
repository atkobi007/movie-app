<script setup>
import MovieTitle from './MovieTitle.vue'
import MovieItem from './MovieItem.vue'

const props = defineProps({
  list: Array,
  title: String,
})

const getData = computed(() => {
  return [{ title: "111", id: '0x99938', type: "" },
  { title: "111", id: '0x99939', type: "" },
  { title: "111", id: '0x99940', type: "" },
  { title: "111", id: '0x99941', type: "" }];//props.list ?? []
})
</script>

<template>
  <div class="item-root">
    <MovieTitle :title="props.title" title-color="white" :isArrow="false"/>
    <!-- <MovieItem v-for="info in [0]" :key="info" :fitHeight="true" :fitWidth="true" score="9.0" hot="654,895"
      typeText="真人" /> -->
    <MovieItem v-for="info in getData" :key="info.id" :fitHeight="false" :fitWidth="false" score="9.0" hot="654,895"
      :typeText="info.type" />
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
