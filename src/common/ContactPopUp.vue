<template>
  <Transition name="fade" appear>
    <div v-if="visible" class="contact-pop-up" @click="handleBackdropClick">
      <Transition name="scale" appear>
        <div class="contact-pop-up-container" @click.stop>
          <div class="contact-pop-up-title">聯絡我們</div>
          <button class="close-btn" @click="close">✕</button>
          <div class="contact-pop-up-form">
            <div class="form-group">
              <div class="contact-pop-up-form-item-title">顧客基本資料</div>
              <div class="contact-pop-up-form-item">
                <label for="name">聯絡人姓名<span>*</span></label>
                <input type="text" id="name" v-model="formData.name" placeholder="請填寫">
              </div>
              <div class="contact-pop-up-form-item">
                <label for="company">公司名稱<span>*</span></label>
                <input type="text" id="company" v-model="formData.company" placeholder="請填寫">
              </div>
              <div class="contact-pop-up-form-item">
                <label for="email">聯絡信箱</label>
                <input type="text" id="email" v-model="formData.email" placeholder="請填寫">
              </div>
              <div class="contact-pop-up-form-item">
                <label for="phone">聯絡電話</label>
                <input type="text" id="phone" v-model="formData.phone" placeholder="請填寫">
              </div>
            </div>
            <div class="form-group">
              <div class="contact-pop-up-form-item-title">租借與方案需求</div>
              <div class="contact-pop-up-form-radio-item">
                <label for="name">AI 導覽機台型號選擇</label>
                <div class="radio-list">
                  <div class="radio-item" v-for="size in sizeOptions" :key="size" @click="formData.size = size" :class="{ 'active': formData.size === size }">{{ size }}</div>
                </div>
              </div>
              <div class="contact-pop-up-form-radio-item">
                <label for="name">租期長度 / 年約（或買斷）</label>
                <div class="radio-list">
                  <div class="radio-item" v-for="due in dueOptions" :key="due" @click="formData.due = due" :class="{ 'active': formData.due === due }">{{ due }}</div>
                </div>
              </div>
              <div class="contact-pop-up-form-radio-item">
                <label for="name">會員方案</label>
                <div class="radio-list">
                  <div class="radio-item" v-for="member in memberOptions" :key="member" @click="formData.member = member" :class="{ 'active': formData.member === member }">{{ member }}</div>
                </div>
              </div>
            </div>
          </div>
          <div class="contact-pop-up-form-submit">
            <button class="submit-btn">送出</button>
          </div>
        </div>
      </Transition>
    </div>
  </Transition>
</template>
<script setup>
import { ref, defineProps, defineEmits, watch } from 'vue'

const props = defineProps({
  modelValue: {
    type: Boolean,
    default: false
  }
})

const formData = ref({
  name: '',
  company: '',
  email: '',
  phone: '',
  size: '',
  due: '',
  member: '',
})

const sizeOptions = ['32吋', '55吋']
const dueOptions = ['7 天', '30 日', '3 個月', '年約（買斷）']
const memberOptions = ['優選會員', '企業會員']

const emit = defineEmits(['update:modelValue'])

const visible = ref(props.modelValue)

const close = () => {
  visible.value = false
  emit('update:modelValue', false)
}

const handleBackdropClick = () => {
  close()
}

// 監聽外部傳入的 modelValue 變化
watch(() => props.modelValue, (newValue) => {
  visible.value = newValue
}, { immediate: true })
</script>
<style lang="scss" scoped>
$primary-color: #353535;

// 背景淡入淡出動畫
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}

// 彈窗縮放動畫
.scale-enter-active, .scale-leave-active {
  transition: all 0.3s ease;
}
.scale-enter-from, .scale-leave-to {
  opacity: 0;
  transform: scale(0.8);
}

.contact-pop-up {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 1000;
  display: flex;
  align-items: center;
  justify-content: center;

  .contact-pop-up-container {
    position: relative;
    width: calc(100% - 48px);
    max-width: 886px;
    max-height: calc(100vh - 200px);
    background-color: #fff;
    border-radius: 16px;
    padding: 46px 64px 64px 64px;
    box-shadow: 0px 10px 20px 0px rgba(0, 0, 0, 0.05);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
    gap: 48px;
    overflow-y: auto;
    margin: 100px 0;




    .close-btn {
      position: absolute;
      top: 53px;
      right: 64px;
      background: none;
      border: none;
      font-size: 30px;
      color: $primary-color;
      cursor: pointer;
      width: 40px;
      height: 40px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 50%;
    }
    .contact-pop-up-title {
      font-size: 40px;
      font-weight: 700;
      line-height: 1.5;
      color: $primary-color;
      text-align: center;
    }
    .contact-pop-up-form {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 32px;
      width: 100%;
      .form-group {
        display: flex;
        flex-direction: column;
        align-items: flex-start;

        gap: 12px;
        width: 100%;
        .contact-pop-up-form-item-title {
          font-size: 20px;
          font-weight: 700;
          line-height: 1.5;
          color: $primary-color;
          margin-bottom: 5px;
        }
        .contact-pop-up-form-item {
          display: flex;
          align-items: center;
          justify-content: center;
          gap: 24px;
          width: 100%;
          label {
            width: 150px;
            font-size: 16px;
            font-weight: 400;
            line-height: 1.5;
            color: $primary-color;
            span {
              color: #FF2A2A;
              margin-left: 4px;
            }
          }
          input {
            flex: 1;
            height: 50px;
            border-radius: 8px;
            padding: 0 16px;
            font-size: 16px;
            font-weight: 400;
            line-height: 1.5;
            color: $primary-color;
            background-color: #FAFAFA;
          }
        }
        .contact-pop-up-form-radio-item {
          display: flex;
          align-items: flex-start;
          justify-content: center;
          flex-direction: column;
          gap: 12px;
          width: 100%;
          label {
            font-size: 16px;
            font-weight: 400;
            line-height: 1.5;
            color: $primary-color;
          }
          .radio-list {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
            .radio-item {
              font-size: 20px;
              font-weight: 700;
              line-height: 1.5;
              color: $primary-color;
              cursor: pointer;
              padding: 12px 24px;
              border-radius: 100px;
              border: 1px solid #E2E2E2;
              &.active {
                border: 1px solid #FDDD59;
                box-shadow: 0 0 0 1px #FDDD59;
                background-color: rgba(253, 221, 89, 0.2);
              }
            }
          }
        }
      }
    }
    .contact-pop-up-form-submit {
      display: flex;
      align-items: center;
      justify-content: center;
      width: 100%;
      .submit-btn {
        width: 300px;
        height: 59px;
        border-radius: 100px;
        background-color: #FDDD59;
        font-size: 18px;
        font-weight: 700;
        line-height: 1.5;
        color: $primary-color;
        cursor: pointer;
        &:disabled {
          background-color: #EDEDED;
          color: #B9B9B9;
          cursor: not-allowed;
        }
      }
    }
  }
}
</style>
