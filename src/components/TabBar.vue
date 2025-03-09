<script setup lang="ts">
import { routeWhiteList } from '@/config/routes'

const { t } = useI18n()
const active = ref(0)
const route = useRoute()

const show = computed(() => route.name && routeWhiteList.includes(route.name))
</script>

<template>
  <van-tabbar v-if="show" v-model="active" route placeholder :safe-area-inset-bottom="true">
    <van-tabbar-item replace to="/">
      {{ t('layouts.home') }}
      <template #icon>
        <div class="i-carbon:home" />
      </template>
    </van-tabbar-item>
    <van-tabbar-item replace to="/find">
      {{ t('layouts.find') }}
      <template #icon>
        <div class="i-carbon:data-analytics" />
      </template>
    </van-tabbar-item>
    <van-tabbar-item replace to="/vip">
      {{ t('layouts.vip') }}
      <template #icon>
        <div class="i-carbon:cube" />
      </template>
    </van-tabbar-item>
    <van-tabbar-item replace to="/hot">
      {{ t('layouts.hot') }}
      <template #icon>
        <div class="i-carbon:sun" />
      </template>
    </van-tabbar-item>

    <van-tabbar-item replace to="/profile">
      {{ t('layouts.profile') }}
      <template #icon>
        <div class="i-carbon:user" />
      </template>
    </van-tabbar-item>
  </van-tabbar>
</template>
