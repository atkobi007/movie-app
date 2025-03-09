<script setup lang="ts">
// import type { PickerColumn } from 'vant'
// import { languageColumns, locale } from '@/utils/i18n'

// const { t } = useI18n()
// const menuItems = computed(() => ([
//   { title: t('menus.mockGuide'), route: 'mock' },
//   { title: t('menus.echartsDemo'), route: 'charts' },
//   { title: t('menus.unocssExample'), route: 'unocss' },
//   { title: t('menus.persistPiniaState'), route: 'counter' },
//   { title: t('menus.keepAlive'), route: 'keepalive' },
//   { title: t('menus.scrollCache'), route: 'scroll-cache' },
//   { title: t('menus.hot'), route: 'hot' },
//   { title: t('menus.404Demo'), route: 'unknown' },
// ]))

// const showLanguagePicker = ref(false)
// const languageValues = ref<Array<string>>([locale.value])
// const language = computed(() => languageColumns.find(l => l.value === locale.value).text)

// function onLanguageConfirm(event: { selectedOptions: PickerColumn }) {
//   locale.value = event.selectedOptions[0].value as string
//   showLanguagePicker.value = false
// }

// const checked = ref<boolean>(isDark.value)

// watchEffect(() => {
//   checked.value = isDark.value
// })

// function toggle(val: boolean) {
//   checked.value = val
//   toggleDark()
// }

/** tab 选中 */
const tabActive = ref(0)
/** ### 搜索 */
function onSearch() {
  // console.log("onSearch");
}
/** ### 菜单 */
function onMenu() {
  // console.log("onMenu")
}

const showPopover = ref(false)
const actions = [
  { text: '选项一', icon: 'add-o' },
  { text: '选项二', icon: 'music-o' },
  { text: '选项三', icon: 'more-o' },
]
const tabsMap = {
  0: defineAsyncComponent(() => {
    return import('@/components/tabs/home.vue')
  }),
  1: defineAsyncComponent(() => {
    return import('@/components/tabs/movie.vue')
  }),
  2: defineAsyncComponent(() => {
    return import('@/components/tabs/tv.vue')
  }),
  3: defineAsyncComponent(() => {
    return import('@/components/tabs/cartoon.vue')
  }),
  4: defineAsyncComponent(() => {
    return import('@/components/tabs/variety-show.vue')
  }),
}

const Component = computed(() => {
  return tabsMap[tabActive.value]
})
</script>

<template>
  <div class="root-main">
    <div
      style="position:fixed;top:0px; display: flex;flex-direction: row;justify-content: space-between;width: 100%;background:white;"
    >
      <div class="tabs-nav tabs-left">
        <div i-carbon:worship />
      </div>
      <van-tabs v-model:active="tabActive" style="width: 68%;" background="white">
        <van-tab v-for="index in 8" :key="index" :title="`标签 ${index}`">
          <!-- 内容 {{ index }} -->
        </van-tab>
      </van-tabs>
      <div class="tabs-nav tabs-right">
        <div i-carbon:zoom-fit @click="onSearch" />
        <van-popover v-model:show="showPopover" :actions="actions" placement="bottom-end">
          <template #reference>
            <div i-carbon:switcher @click="onMenu" />
          </template>
        </van-popover>
      </div>
    </div>
    <keep-alive>
      <component :is="Component" :key="tabActive" />
    </keep-alive>
  </div>

  <!-- <div class="page-wrapper-tb">
    <div class="page-wrapper-lr">
      <van-cell-group :title="t('menus.basicSettings')" :border="false" :inset="true">
        <van-cell center :title="t('menus.darkMode')">
          <template #right-icon>
            <van-switch v-model="checked" size="20px" aria-label="on/off Dark Mode" @change="toggle" />
          </template>
        </van-cell>

        <van-cell is-link :title="t('menus.language')" :value="language" @click="showLanguagePicker = true" />
      </van-cell-group>

      <van-cell-group :title="t('menus.exampleComponents')" :border="false" :inset="true">
        <template v-for="item in menuItems" :key="item.route">
          <van-cell :title="item.title" :to="item.route" is-link />
        </template>
      </van-cell-group>

      <van-popup v-model:show="showLanguagePicker" position="bottom">
        <van-picker v-model="languageValues" :columns="languageColumns" @confirm="onLanguageConfirm"
          @cancel="showLanguagePicker = false" />
      </van-popup>
    </div>
  </div> -->
</template>

<style lang="less" scoped>
.root-main {
  width: 100%;
  height: 100%;
  padding-top: 45px;
}

.tabs-nav {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

.tabs-left {
  width: 10%;
  padding-left: 6px;
}

[i-carbon\:worship=''] {
  height: 30px;
  width: 30px;
}

.tabs-right {
  width: 22%;
  justify-content: flex-end;
  padding-right: 6px;
  gap: 10px;
}

[i-carbon\:zoom-fit=''],
[i-carbon\:switcher=''] {
  width: 26px;
  height: 26px;
}
</style>

<route lang="json5">
{
  name: 'home',
  meta: {
    title: '主页',
    i18n: 'menus.home'
  },
}
</route>
