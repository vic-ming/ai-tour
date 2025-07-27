<template>
  <div id="features-section" class="space-ai-view">
    <div class="space-ai-view-container container">
      <div class="space-ai-view-title" data-aos="fade-up">
        {{ $t('spaceAI.title') }}<br>{{ $t('spaceAI.subtitle') }}
      </div>
      <div class="space-ai-view-box" :class="{ 'space-ai-view-box-en': !isZH }" data-aos="fade-right" data-aos-delay="200">
        <div class="space-ai-view-box-title">
          <img v-if="isZH" src="@/assets/images/icon_user.svg" alt="user">
          {{ $t('spaceAI.features.assistant.title') }}
        </div>
        <div class="space-ai-view-box-description">{{ $t('spaceAI.features.assistant.description') }}</div>
      </div>
      <div class="space-ai-view-box" :class="{ 'space-ai-view-box-en': !isZH }" data-aos="fade-left" data-aos-delay="400">
        <div class="space-ai-view-box-title">
          <img v-if="isZH" src="@/assets/images/icon_map.svg" alt="map">
          {{ $t('spaceAI.features.map.title') }}
        </div>
        <div class="space-ai-view-box-description" v-html="$t('spaceAI.features.map.description')"></div>
      </div>
      <div class="space-ai-view-box" :class="{ 'space-ai-view-box-en': !isZH }" data-aos="fade-right" data-aos-delay="600">
        <div class="space-ai-view-box-title">
          <img v-if="isZH" src="@/assets/images/icon_point.svg" alt="point">
          {{ $t('spaceAI.features.recommendation.title') }}
        </div>
        <div class="space-ai-view-box-description">{{ $t('spaceAI.features.recommendation.description') }}</div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { useI18n } from 'vue-i18n';
import { computed } from 'vue';
const { locale } = useI18n();
const isZH = computed(() => locale.value === 'zh-TW');
</script>
<style lang="scss" scoped>
$primary-color: #353535;
.space-ai-view {
  width: 100%;
  min-height: 700px;
  background-image: url('@/assets/images/space_ai_bg.webp');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  display: flex;
  flex-direction: column;
  justify-content: center;
  .space-ai-view-container {
    .space-ai-view-title {
      font-size: 40px;
      font-weight: 700;
      color: $primary-color;
      line-height: 1.5;
      margin-bottom: 20px;
    }
    .space-ai-view-box {
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      justify-content: center;
      gap: 8px;
      padding: 24px;
      background: linear-gradient(90deg, rgba(13, 192, 222, 0.9) 0%, rgba(110, 204, 169, 0.9) 51.44%, rgba(252, 222, 91, 0.9) 100%);
      width: 500px;
      margin-bottom: 20px;
      box-sizing: border-box;

      &:nth-child(3) {
        position: relative;
        left: 307px;
      }
      &:nth-child(4) {
        position: relative;
        left: 104px;
      }
      &.space-ai-view-box-en {
        width: 570px;
        &:nth-child(3) {
          width: 545px;
        }
        &:nth-child(4) {
          width: 582px;
        }
      }
      .space-ai-view-box-title {
        display: flex;
        align-items: center;
        gap: 8px;
        font-size: 24px;
        font-weight: 700;
        color: #fff;
        line-height: 1.5;
        img {
          width: 24px;
          height: 24px;
        }
      }
      .space-ai-view-box-description {
        font-size: 16px;
        font-weight: 400;
        color: #fff;
        line-height: 1.5;
      }
    }
  }
}
</style>
