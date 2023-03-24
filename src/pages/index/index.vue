<template>
  <div class="index">
    <nut-searchbar v-model="searchValue" background="#3960c5">
      <template v-slot:leftin>
        <Search2 />
      </template>
      <template v-slot:rightin>
        <Photograph />
      </template>
      <template v-slot:rightout>
        <Message />
      </template>
    </nut-searchbar>
    <nut-swiper :init-page="page" :pagination-visible="true" pagination-color="#426543" auto-play="5000" :height="150">
      <nut-swiper-item>
        <img src="https://storage.360buyimg.com/jdc-article/NutUItaro34.jpg" alt="" />
      </nut-swiper-item>
      <nut-swiper-item>
        <img src="https://storage.360buyimg.com/jdc-article/NutUItaro2.jpg" alt="" />
      </nut-swiper-item>
      <nut-swiper-item>
        <img src="https://storage.360buyimg.com/jdc-article/welcomenutui.jpg" alt="" />
      </nut-swiper-item>
      <nut-swiper-item>
        <img src="https://storage.360buyimg.com/jdc-article/fristfabu.jpg" alt="" />
      </nut-swiper-item>
    </nut-swiper>
    <nut-grid>
      <nut-grid-item text="文字"><Dongdong /></nut-grid-item>
      <nut-grid-item text="文字"><Dongdong /></nut-grid-item>
      <nut-grid-item text="文字"><Dongdong /></nut-grid-item>
      <nut-grid-item text="文字"><Dongdong /></nut-grid-item>
      <nut-grid-item text="文字"><Dongdong /></nut-grid-item>
      <nut-grid-item text="文字"><Dongdong /></nut-grid-item>
      <nut-grid-item text="文字"><Dongdong /></nut-grid-item>
      <nut-grid-item text="文字"><Dongdong /></nut-grid-item>
    </nut-grid>

    <nut-divider :style="{ color: '#333', borderColor: '#f4f4f4', padding: '0 16px' }">商品列表</nut-divider>

    <!-- <nut-list> -->
    <nut-card
      class="home-nut-card"
      v-for="i in 10"
      :key="i"
      :img-url="state.imgUrl"
      :title="state.title"
      :price="state.price"
      :vipPrice="state.vipPrice"
      :shopDesc="state.shopDesc"
      :delivery="state.delivery"
      :shopName="state.shopName"
    ></nut-card>
    <!-- </nut-list> -->

    <nut-tabbar v-model="activeTab" @tab-switch="tabSwitch" bottom safe-area-inset-bottom placeholder>
      <nut-tabbar-item v-for="(item, index) in tabList" :key="index" :name="item.name" :tab-title="item.title" :icon="item.icon" :value="item.value || null"> </nut-tabbar-item>
    </nut-tabbar>
  </div>
</template>

<script setup>
import { Home, Category, Find, Cart, My, Search2, Photograph, Message, Dongdong } from "@nutui/icons-vue-taro";
import { h, ref, reactive } from "vue";

const message = ref("hello world~~");

const searchValue = ref("");

const activeTab = ref("home");
const tabList = reactive([
  {
    title: "首页",
    icon: h(Home),
    name: "home"
  },
  {
    title: "分类",
    icon: h(Category),
    name: "category"
  },
  {
    title: "发现",
    icon: h(Find),
    name: "find",
    value: 168
  },
  {
    title: "购物车",
    icon: h(Cart),
    name: "cart"
  }
]);

const state = reactive({
  imgUrl: "//img10.360buyimg.com/n2/s240x240_jfs/t1/210890/22/4728/163829/6163a590Eb7c6f4b5/6390526d49791cb9.jpg!q70.jpg",
  title: "活蟹】湖塘煙雨 阳澄湖大闸蟹公4.5两 母3.5两 4对8只 鲜活生鲜螃蟹现货水产礼盒海鲜水",
  price: "388",
  vipPrice: "378",
  shopDesc: "自营",
  delivery: "厂商配送",
  shopName: "阳澄湖大闸蟹自营店>"
});

function tabSwitch(item, index) {
  console.log("tabSwitch : ", item, index);
}

function back() {}
function title() {}
</script>

<style lang="scss">
img {
  display: block;
  width: 100%;
  height: 100%;
}
.home-nut-card {
  margin-bottom: 20px;
}
</style>
