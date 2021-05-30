<!-- npm i --save swiper@5.x vue-awesome-swiper
  → vue-awesome-swiperはvue2から使える。
  vue3では試していない。（エラーが出たので、vue2に切り替えた）
（公式）https://github.com/surmon-china/vue-awesome-swiper
  swiper.jsもインストールする必要がある。
  読み込むcssはswiperのバージョンによってディレクトリが異なるので注意
-->

<template>
  <div class="contents">
    <h1>VueAwesomeSwiperを使う</h1>
    <swiper :options="swiperOption">
      <swiper-slide
        >Slide 1
        <img src="../assets/image_1.jpg" />
      </swiper-slide>
      <swiper-slide
        >Slide 2
        <img src="../assets/image_2.jpg" />
      </swiper-slide>
      <swiper-slide
        >Slide 3
        <img src="../assets/image_3.jpg" />
      </swiper-slide>
      ...
    </swiper>
  </div>
  <!-- /.contents -->
</template>

<script>
import { Swiper, SwiperSlide } from "vue-awesome-swiper";

// スタイルもモジュールから読み込む
import "swiper/css/swiper.css";

export default {
  data() {
    return {
      swiperOption: {
        effect: "flip", // 切り替わりの見た目変化
        grabCursor: true, // カーソルがグローブになる。
        pagination: {
          el: ".swiper-pagination",
          clickable: true,
        },
        slidesPerView: 1, // 表示枚数
        centeredSlides: true,
        loop: true,
        autoplay: {
          delay: 2000,
          disableOnInteraction: false,
        },
      },
    };
  },
  components: {
    Swiper,
    SwiperSlide,
  },
};
</script>

<style lang="scss" scoped>
h1 {
  text-align: center;
}

// swiperの全体スタイル
.swiper-container {
  width: 300px;
  height: 300px;
}

// // スライドの各カードのスタイル
.swiper-slide {
  & > img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}
</style>
