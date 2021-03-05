<template>
  <div class="home">
    <!-- 轮播图 -->
    <van-swipe class="my-swipe" :autoplay="3000" indicator-color="white">
      <van-swipe-item v-for="(image, index) in images" :key="index">
        <img v-lazy="image" />
      </van-swipe-item>
    </van-swipe>
    <!-- 功能 -->
    <div class="padding-t-b">
      <van-grid :gutter="10">
        <van-grid-item
          v-for="value in gridList"
          :key="value.value"
          icon="photo-o"
          :text="value.text"
        />
      </van-grid>
    </div>
    <!-- 最近几条数据 -->
    <!-- git push test -->
    <div class="text-align-left">
      <van-cell-group>
        <van-cell title="今日支出" value="￥100.00" />
        <van-cell title="单元格" value="内容" label="描述信息" />
      </van-cell-group>
      <van-cell-group>
        <van-cell title="今日收益" value="￥100.00" />
        <van-cell title="单元格" value="内容" label="描述信息" />
      </van-cell-group>
    </div>

    <!-- tabbar -->
    <van-tabbar v-model="active" @change="onChangeTab">
      <van-tabbar-item icon="home-o">首页</van-tabbar-item>
      <van-tabbar-item icon="search" dot>股市/基金</van-tabbar-item>
      <van-tabbar-item icon="friends-o" badge="5">记事本</van-tabbar-item>
      <van-tabbar-item icon="setting-o" badge="20">我的</van-tabbar-item>
    </van-tabbar>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "Home",
  data() {
    return {
      images: [
        "https://img01.yzcdn.cn/vant/apple-1.jpg",
        "https://img01.yzcdn.cn/vant/apple-2.jpg",
      ],
      active: 0,
      gridList: [
        {
          value: "0",
          text: "记账",
        },
        {
          value: "1",
          text: "收入",
        },
        {
          value: "2",
          text: "支出",
        },
        {
          value: "3",
          text: "预算",
        },
      ],
    };
  },
   methods: {
    onChangeTab(index) {
      Notify({ type: 'primary', message: index });
    },
  },
  components: {
    HelloWorld,
  },
};
</script>

<style>
body{
  background-color: aliceblue;
}
.my-swipe .van-swipe-item {
  width: 100%;
  height: 200px;
  color: #fff;
  font-size: 20px;
  line-height: 150px;
  text-align: center;
  background-color: #39a9ed;
}
.my-swipe .van-swipe-item img {
  width: 100%;
  height: 200px;
}
.padding-t-b {
  padding: 20px 0;
}
.text-align-left {
  text-align: left;
}
</style>
