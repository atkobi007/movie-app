<script setup>
const props = defineProps({
  title: String,
  titleColor: String,
  subTitle: {
    type: String,
    default: '',
  },
  subTitleColor: String,
  isArrow: {
    type: Boolean,
    default: true
  },
  arrowColor: {
    type: String,
    default: 'gray',
  },
  backgroundColor: String,
})

/** ### 设置背景颜色 */
const setBackGroundColor = computed(() => {
  if (props.backgroundColor) {
    return {
      'background-color': props.backgroundColor,
    }
  }
  return {}
})

/** ### 设置标题颜色 */
const setTitleColor = computed(() => {
  if (props.titleColor) {
    return {
      color: props.titleColor,
    }
  }
  return {}
})

/** ### 设置子标题颜色 */
const setSubTitleColor = computed(() => {
  if (props.subTitleColor) {
    return {
      color: props.subTitleColor,
    }
  }
  return {}
})

/** ### 设置子标题颜色 */
const setArrowColor = computed(() => {
  if (props.arrowColor) {
    return {
      color: props.arrowColor,
    }
  }
  return {}
})
</script>

<template>
  <div class="title-root" :style="setBackGroundColor">
    <span class="title-root-0" :style="setTitleColor">{{ title }}</span>
    <div class="sub-title-root">
      <span v-if="!!props.subTitle" :style="setSubTitleColor">{{ subTitle }}</span>
      <span v-if="props.isArrow" :style="setArrowColor" i-carbon:chevron-right />
    </div>
  </div>
</template>

<style scoped>
.title-root {
  width: 100%;
  height: 30px;
  display: flex;
  flex-direction: row;
  align-items: center;
}

.title-root-0 {
  font-weight: 400;
  font-size: 20px;
}

.sub-title-root {
  display: flex;
  flex-direction: row;
  align-items: center;
}

.title-root-pos {
  justify-content: space-between;
}
</style>
