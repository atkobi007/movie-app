<script setup>

</script>

<template>
  <div class="item">
    <div class="item-cover">
      <img src="https://fastly.jsdelivr.net/npm/@vant/assets/apple-1.jpeg" width="100%" height="100%">
      <div class="item-container">
        <div>
          <van-icon name="fire" class="content-bold" style="margin-right: 5px;" />
          <span class="content-bold">6058</span>
        </div>
        <span class="content-bold">00:00:42</span>
      </div>
    </div>
    <div class="item-title van-ellipsis">
      标题信息标题信息标题信息标题信息标题信息
    </div>
  </div>
</template>

<style scoped>
.item {
  width: 174px;
  height: auto;
}

.item-cover {
  width: 174px;
  height: 100px;
  position: relative;
  background-color: yellow;
}

.item-container {
  width: 100%;
  height: 20px;
  position: relative;
  bottom: 20px;
  font-size: 10px;
  background-image: linear-gradient(to top, rgba(0, 0, 0, 0.9), rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.01));
  padding-left: 6px;
  padding-right: 6px;

  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
}

.content-bold {
  font-weight: bold;
  color: rgba(255, 255, 255, 0.8);
}

.item-title {
  width: 100%;
  height: 30px;
  line-height: 40px;
  font-size: 14px;
  color: white;
}
</style>
