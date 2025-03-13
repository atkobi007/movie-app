<script setup>
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
</script>

<template>
  <div class="root-home">
    <van-swipe :autoplay="3000" lazy-render class="swiper-container">
      <van-swipe-item v-for="image in images" :key="image">
        <div style="height: 190px;width: 100%;" :style="imageStyle(image)">
          <div class="custom-item">
            标题
          </div>
        </div>
      </van-swipe-item>
      <template #indicator="{ active, total }">
        <div class="custom-indicator">
          <div
            v-for="(item, ix) in total" :key="item" class="custom-indicator-item"
            :class="{ 'custom-indicator-item-active': active === ix }"
          />
        </div>
      </template>
    </van-swipe>
    <div>HOME</div>
    <div>BOTTOm</div>
  </div>
</template>

<style scoped>
.root-home {
  width: 100%;
  height: 1000px;
  background-color: antiquewhite;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.swiper-container {
  height: 190px;
  width: 100%;
  position: relative;
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
