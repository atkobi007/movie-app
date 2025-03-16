<script setup>

const props = defineProps({
  fitHeight: Boolean,//宽度100%(220px)
  fitWidth: Boolean,//宽度100%
  score: String,//评分
  hot: String,//热门数
  typeText: String,//类型
})

/** ### 设置高度 */
const setItemCoverCls = computed(() => {
  if (props.fitWidth) {
    return ['item-cover-width-fill'];
  }
  if (props.fitHeight) {
    return ['item-cover-fill']
  }
  return ['item-cover']
})

/** ### 设置高度 */
const setItemCls = computed(() => {
  if (props.fitWidth) {
    return ['item-fill']
  }
  return ['item']
})
/** ### 设置标题和类型样式 */
const setItemTitleType = computed(() => {
  if (props.fitWidth) {
    return ['item-title-type1'];
  }
  return ['item-title-type']
})

/** ### 设置类型样式 */
const setItemType = computed(() => {
  if (props.fitWidth) {
    return ['item-type1'];
  }
  return ['item-type']
})

</script>

<template>
  <div class="item" :class="setItemCls">
    <div class="item-cover border-radius-top" :class="setItemCoverCls">
      <img class="border-radius-top" src="https://fastly.jsdelivr.net/npm/@vant/assets/apple-1.jpeg" width="100%"
        height="100%">
      <div class="item-container border-radius-bottom">
        <div class="content-height">
          <div class="content-hot">{{ score }}</div>
          <van-icon name="fire" class="content-bold" style="margin-right: 5px;" />
          <span class="content-bold">{{ hot }}</span>
        </div>
        <span class="content-bold">00:00:42</span>
      </div>
    </div>
    <div :class="setItemTitleType">
      <span class="item-title van-ellipsis">标题信息标题信息标题信息标题信息标题信息</span>
      <span v-if="!!typeText" :class="setItemType">{{ typeText }}</span>
    </div>
  </div>
</template>

<style scoped>
.item {
  width: 174px;
  height: auto;
  border-radius: 16px;
}

.item-fill {
  width: 100%;
  height: auto;
  border-radius: 16px;
}

.item-cover {
  width: 174px;
  height: 100px;
  position: relative;
  background-color: yellow;
}

.border-radius-top {
  border-radius: 4px 4px 0px 0px;
}

.border-radius-bottom {
  /* border-radius: 0px 0px 4px 4px; */
}

.item-cover-width-fill {
  width: 100%;
  height: 170px;
  position: relative;
  background-color: yellow;
}

.item-cover-fill {
  width: 100%;
  height: 220px;
  position: relative;
  background-color: yellow;
}

.item-container {
  width: 100%;
  height: 20px;
  position: relative;
  bottom: 24px;
  font-size: 10px;
  background-image: linear-gradient(to top, rgba(0, 0, 0, 0.9), rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.01));
  padding-left: 6px;
  padding-right: 6px;

  /* border-radius: 0px 0px 6px 6px; */

  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
}

.content-height {
  height: 57px;
}

.content-hot {
  color: #ff743d;
  margin-bottom: 5px;
  font-size: 16px;
  font-weight: bold;
}

.content-bold {
  font-weight: bold;
  color: rgba(255, 255, 255, 0.8);
}

.item-title {
  height: 30px;
  line-height: 40px;
  font-size: 16px;
  color: rgba(255, 255, 255, 0.9);
}

.item-type {
  font-size: 10px;
  color: rgba(255, 255, 255, 0.6);
}

.item-title-type {
  display: flex;
  flex-direction: column;
}

.item-title-type1 {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

.item-type1 {
  font-size: 12px;
  color: gray;
  height: 30px;
  line-height: 40px;
}
</style>
