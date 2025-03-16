<script setup>
import MovieType1 from '../common/MovieType1.vue'
import MovieType2 from '../common/MovieType2.vue'

const images = ref([
  'https://fastly.jsdelivr.net/npm/@vant/assets/apple-1.jpeg',
  'https://fastly.jsdelivr.net/npm/@vant/assets/apple-2.jpeg',
  'https://fastly.jsdelivr.net/npm/@vant/assets/apple-1.jpeg',
  'https://fastly.jsdelivr.net/npm/@vant/assets/apple-2.jpeg',
  'https://fastly.jsdelivr.net/npm/@vant/assets/apple-1.jpeg',
  'https://fastly.jsdelivr.net/npm/@vant/assets/apple-2.jpeg',
])

/** ### 背景图片 */
function imageStyle(img) {
  return {
    'background-image': `url(${img})`,
    'background-size': '100% 100%',
  }
}

const data = [
  { title: "今日热门", list: [1, 2, 3, 4], type: 1 },
  { title: "电影", list: [1, 2, 3, 4], type: 2 },
  { title: "电视剧", list: [1, 2, 3, 4], type: 3 },
  { title: "综艺", list: [1, 2, 3, 4], type: 4 },
  { title: "动漫", list: [1, 2, 3, 4], type: 5 }
]

const getItemComponent = (type) => {
  if (type === 1) {
    return MovieType1;
  }
  return MovieType2;
}

</script>

<template>
  <div class="root-home">
    <van-swipe :autoplay="3000" lazy-render class="swiper-container">
      <van-swipe-item v-for="image in images" :key="image">
        <div class="swiper-container-conver" :style="imageStyle(image)">
          <div class="custom-item">
            标题
          </div>
        </div>
      </van-swipe-item>
      <template #indicator="{ active, total }">
        <div class="custom-indicator">
          <div v-for="(item, ix) in total" :key="item" class="custom-indicator-item"
            :class="{ 'custom-indicator-item-active': active === ix }" />
        </div>
      </template>
    </van-swipe>
    <div>
      <template v-for="item in data" :key="item.type">
        <MovieType1 v-if="item.type === 1" :list="item.list" :title="item.title" />
        <MovieType2 v-else :list="item.list" :title="item.title" />
      </template>
    </div>
    <div>BOTTOm</div>
  </div>
</template>

<style scoped>
.root-home {
  width: 100%;
  height: auto;
  background-color: rgba(0, 0, 0, 0.9);
  display: flex;
  flex-direction: column;
  /* justify-content: space-between; */
}

.swiper-container {
  height: 190px;
  width: 100%;
  position: relative;
}

.swiper-container-conver {
  height: 190px;
  width: 100%;
}

.custom-item {
  height: 40px;
  width: 100%;
  position: absolute;
  bottom: 0px;
  background-image: linear-gradient(to top, rgba(0, 0, 0, 0.8), rgba(255, 255, 255, 0.1));
  display: flex;
  flex-direction: row;
  align-items: center;
  color: white;
}

.custom-indicator {
  position: absolute;
  right: 5px;
  bottom: 5px;
  padding: 2px 5px;
  font-size: 12px;
  /* background: rgba(0, 0, 0, 0.1); */
  display: flex;
  flex-direction: row;
  gap: 6px;
}

.custom-indicator-item {
  width: 8px;
  height: 1px;
  background-color: gray;
}

.custom-indicator-item-active {
  background-color: #00bdff;
}
</style>
