<template>
  <div class="integrate-view">
    <div class="integrate-view-container container">
      <div class="integrate-view-title" data-aos="fade-up">
        <span>{{ $t('integrate.title.brand') }}</span>
        <span v-html="$t('integrate.title.subtitle')"></span>
      </div>
      <div class="integrate-view-content">
        <div
          class="integrate-view-content-item"
          v-for="(item, index) in data"
          :key="index"
          :style="{ backgroundImage: `url(${item.img})` }"
          data-aos="fade-down"
          :data-aos-delay="index * 200"
        >
          <div class="integrate-view-content-item-title">
            <div v-html="$t(`integrate.features.${item.key}.title`)"></div>
          </div>
          <div class="integrate-view-content-item-description">
            <div v-html="$t(`integrate.features.${item.key}.description`)"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import img_1 from '@/assets/images/integrate-1.webp'
import img_2 from '@/assets/images/integrate-2.webp'
import img_3 from '@/assets/images/integrate-3.webp'
const data = [
    {
        key: 'immersive',
        img: img_1,
    },
    {
        key: 'aiCharacter',
        img: img_2,
    },
    {
        key: 'realtime',
        img: img_3,
    }
]
</script>
<style lang="scss" scoped>
$primary-color: #353535;
.integrate-view {
  padding: 60px 0;
  background-color: #fafafa;
  .integrate-view-container {
    display: flex;
    flex-direction: column;
    gap: 57px;
    .integrate-view-title {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 4px;
      justify-content: center;
      span {
        display: block;
        text-align: center;
      }
      span:first-child {

        font-size: 24px;
        font-weight: 700;
        background: linear-gradient(90.03deg, #0DC0DE 1.09%, #6ECCA9 52.21%, #FCDE5B 100.46%);
        background-clip: text;
        -webkit-background-clip: text;
        color: transparent;
        line-height: 1.5;
      }
      span:last-child {
        font-size: 40px;
        font-weight: 700;
        color: $primary-color;
        line-height: 1.5;
      }
    }
    .integrate-view-content {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 24px;
      .integrate-view-content-item {
        height: 500px;
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
        border-radius: 16px;
        padding: 32px 24px;
        display: flex;
        align-items: flex-start;
        flex-direction: column;
        gap: 8px;
        box-sizing: border-box;
        color: #fff;
        .integrate-view-content-item-title {
          font-size: 20px;
          font-weight: 700;
          line-height: 1.5;
        }
        .integrate-view-content-item-description {
          font-size: 16px;
          font-weight: 400;
          line-height: 1.5;
        }
      }
    }
  }
}

</style>
