<template>
  <div class="chat-view">
    <div class="chat-view-circle" data-aos="zoom-in">
      <div class="chat-view-circle-content">
        <div class="chat-view-circle-content-title">
          {{ $t('chat.title') }}
        </div>
        <div class="chat-view-circle-content-description">
          <span v-html="$t('chat.description')"></span>
        </div>
      </div>
      <div class="ripple ripple-1"></div>
      <div class="ripple ripple-2"></div>
      <div class="ripple ripple-3"></div>
    </div>
    <div class="chat-view-video">
      <video src="@/assets/video/chat_video_1.webm" autoplay muted loop></video>
    </div>
  </div>
</template>
<script setup>

</script>
<style lang="scss" scoped>
.chat-view {
  background-image: url('@/assets/images/chat-bg.webp');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  height: 700px;
  width: 100%;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  .chat-view-circle {
    position: relative;
    right: 170px;
    .chat-view-circle-content {
      width: 507px;
      height: 507px;
      background: linear-gradient(180deg, #0DC0DE 0%, #6ECCA9 51.44%, #FCDE5B 100%);
      border-radius: 50%;
      position: relative;
      z-index: 1;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 16px;
      .chat-view-circle-content-title {
        font-size: 40px;
        font-weight: 700;
        color: #fff;
        line-height: 1.5;
        text-align: center;
        width: 400px;
      }
      .chat-view-circle-content-description {
        font-size: 20px;
        line-height: 1.5;
        color: #fff;
        text-align: center;
      }
    }
    .ripple {
      position: absolute;
      top: 50%;
      left: 50%;
      width: 100%;
      height: 100%;
      border-radius: 50%;
      background: linear-gradient(180deg, #0DC0DE 0%, #6ECCA9 51.44%, #FCDE5B 100%);
      transform: translate(-50%, -50%) scale(0);
      animation: rippleAnimation 3s infinite ease-out;


      &.ripple-1 {
        animation-delay: 0s;
      }

      &.ripple-2 {
        animation-delay: 1s;
      }

      &.ripple-3 {
        animation-delay: 2s;
      }
    }
  }
  .chat-view-video {
    position: absolute;
    top: 36px;
    right: -9vw;
    video {
      width: 57vw;
      object-fit: cover;
    }
  }
}

@keyframes rippleAnimation {
  0% {
    transform: translate(-50%, -50%) scale(0);
    opacity: 1;
  }
  70% {
    transform: translate(-50%, -50%) scale(1.2);
    opacity: 0.3;
  }
  100% {
    transform: translate(-50%, -50%) scale(1.4);
    opacity: 0;
  }
}
@media (max-width: 1196px) {
  .chat-view {
    .chat-view-circle {
      right: 110px;
      .chat-view-circle-content {
        width: 400px;
        height: 400px;
      }
    }
    .chat-view-video {
      right: -7vw;
    }
  }
}
@media (max-width: 768px) {
  .chat-view {
    align-items: flex-start;
    height: 711px;
    .chat-view-circle {
      right: 0;
      margin-top: 87px;
      .chat-view-circle-content {
        width: 247px;
        height: 247px;
        .chat-view-circle-content-title {
          font-size: 32px;
          width: 163px;
        }
        .chat-view-circle-content-description {
          font-size: 16px;
          width: 163px;
        }
      }
    }
    .chat-view-video {
      right: calc(50% - 213px);
      bottom: -385px;
      top: auto;
      video {
        width: 427px
      }
    }
  }
}
</style>