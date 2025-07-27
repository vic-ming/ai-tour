<template>
  <div id="usecase-section" class="solution-view">
    <div class="space-ai-view-container container">
      <div class="solution-view-title" data-aos="fade-up">
        {{ $t('solution.title') }}
      </div>
      <div class="solution-view-description" data-aos="fade-up" data-aos-delay="100">
        {{ $t('solution.description') }}
      </div>
    </div>

    <swiper
      :modules="modules"
      :space-between="24"
      slides-per-view="auto"
      :loop="false"
      :autoplay="{
        delay: 5000,
        disableOnInteraction: false,
      }"
      :pagination="false"
      :navigation="false"
      :free-mode="true"
      :observer="true"
      :observe-parents="true"
      :mousewheel="true"
      class="solution-swiper"
      data-aos="fade-up"
      data-aos-delay="200"
    >
      <swiper-slide class="slide-item" v-for="(item, index) in slides" :key="index">
        <div class="slide-content">
          <div class="slide-content-img" :style="{ backgroundImage: `url(${item.img})` }">
            <div class="slide-content-title" v-if="item.key">
              {{ $t(`solution.cases.${item.key}.title`) }}
            </div>
            <div class="slide-content-play-mask" @click="emit('openVideoPopUp')">
              <img src="@/assets/images/play-opacity.svg" alt="play">
              {{ $t('common.buttons.browseCase') }}
            </div>
          </div>
          <div v-if="item.key" v-html="$t(`solution.cases.${item.key}.description`)"></div>
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>
<script setup>
import { defineEmits } from 'vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Mousewheel, Autoplay, FreeMode } from 'swiper/modules'
import solution1 from '@/assets/images/solution_1.webp'
import solution2 from '@/assets/images/solution_2.webp'
import solution3 from '@/assets/images/solution_3.webp'
import solution4 from '@/assets/images/solution_4.webp'
import solution5 from '@/assets/images/solution_5.webp'

// 引入模塊
const modules = [Mousewheel, Autoplay, FreeMode]

const emit = defineEmits(['openVideoPopUp'])

// 示例數據
const slides = [
  {
    key: 'exhibition',
    img: solution1
  },
  {
    key: 'mall',
    img: solution2
  },
  {
    key: 'museum',
    img: solution3
  },
  {
    key: 'office',
    img: solution4
  },
  {
    img: solution5
  },
]
</script>
<style lang="scss" scoped>
$primary-color: #353535;
.solution-view {
  padding: 60px 0;
  background-color: #fafafa;
  .space-ai-view-container {
    margin-bottom: 57px;
    .solution-view-title {
      font-size: 40px;
      font-weight: 700;
      color: $primary-color;
      line-height: 1.5;
      margin-bottom: 12px;
    }
    .solution-view-description {
      font-size: 24px;
      font-weight: 700;
      color: $primary-color;
      line-height: 1.5;
    }
  }
}

.solution-swiper {
  width: 100%;
  padding: 0  calc((100% - 1196px) / 2);
  box-sizing: border-box;

  .slide-content {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    height: 100%;
    width: 486px;
    border-radius: 10px;
    gap: 24px;
    .slide-content-img {
      width: 100%;
      height: 100%;
      border-radius: 10px;
      color: white;
      height: 300px;
      position: relative;

      .slide-content-title {
        font-size: 24px;
        line-height: 1.5;
        font-weight: bold;
        position: absolute;
        bottom: 20px;
        left: 28px;
        color: white;
      }
    }
    .slide-content-description {
      font-size: 16px;
      line-height: 1.5;
      color: $primary-color;
    }
    .slide-content-play-mask {
      cursor: pointer;
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      display: none;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 4px;
      font-size: 24px;
      font-weight: 700;
      color: white;
      line-height: 1.5;
      img {
        width: 80px;
        height: 80px;
        transition: all 0.3s ease;
      }
      &:hover {
        img {
          width: 100px;
          height: 100px;
        }
      }
    }
  }
  .slide-item {
    width: auto;
    &:last-child {
      .slide-content-play-mask{
        display: flex;
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        border-radius: 10px;
      }
    }
  }
}
@media (max-width: 1196px) {
  .solution-swiper {
    padding: 0 16px;
  }
}
</style>
