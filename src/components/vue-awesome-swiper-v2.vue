<!-- npm i --save swiper@5.x vue-awesome-swiper
  → vue-awesome-swiperはvue2から使える。
  vue3では試していない。（エラーが出たので、vue2に切り替えた）
（公式）https://github.com/surmon-china/vue-awesome-swiper
  swiper.jsもインストールする必要がある。swiperはversion5が推奨されている
  読み込むcssはswiperのバージョンによってディレクトリが異なるので注意
-->

<template>
  <div class="contents">
    <h1>VueAwesomeSwiperを使う</h1>
    <swiper :options="swiperOption">
      <swiper-slide>
        <img src="../assets/image_1.jpg" />
      </swiper-slide>
      <swiper-slide>
        <img src="../assets/image_2.jpg" />
      </swiper-slide>
      <swiper-slide>
        <img src="../assets/image_3.jpg" />
      </swiper-slide>
    </swiper>
  </div>
  <!-- /.contents -->
</template>

<script>
import { Swiper, SwiperSlide } from "vue-awesome-swiper";

// スタイル読み込み
import "swiper/css/swiper.css";

export default {
  data() {
    return {
      // optionはtemplateにディレククティブ的に書くこともできる。
      // 例 <swiper :slides-per-viwe="3" :space-between="10"></swiper>

      // 下のようにdataにまとめて渡すこともできる。
      swiperOption: {
        freeMode: true,
        loop: true,
        loopedSlides: 6,
        slidesPerView: 3,
        speed: 3000,
        autoplay: {
          delay: 0,
        },

        // スライドが止まらず、ひたすら動くための処理
        // （参考）https://tedate.jp/wp-tips/swiper-horizontal-scroll-continuously
        on: {
          slideChangeTransitionStart: function () {
            const wrapper = document.querySelector(".swiper-wrapper");
            wrapper.style.transitionTimingFunction = "linear";
          },
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
* {
  margin: 0;
}
h1 {
  text-align: center;
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
