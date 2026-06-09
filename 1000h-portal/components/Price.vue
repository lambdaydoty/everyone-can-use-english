<template>
  <div class="price">
    <div class="container m-auto">
      <div class="gap-[48px] grid grid-cols-1 md:grid-cols-2">
        <div class="intro">
          <div class="title text-[20px] md:text-[32px]">增值體驗</div>
          <div class="subtitle text-[14px] md:text-[16px]">
            Enjoy App
            會根據使用的功能按量計費，新使用者消耗完初期餘額後，你可以透過充值來享受更多服務
          </div>

          <div class="items">
            <div v-for="(item, index) in items" :key="index" class="item">
              <span>
                <img src="/portal-static/icon/check.svg" />
              </span>
              <span class="text-[14px] md:text-[16px]">{{ item }}</span>
            </div>
          </div>
        </div>

        <div class="self-center">
          <img
            class="md:h-[356px] lg:hidden"
            src="/portal-static/images/payment.png"
          />

          <img
            class="hidden lg:block"
            src="/portal-static/images/payment-2.png"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name: "Price",
};
</script>

<script lang="ts" setup>
const items = ref([
  "跟讀更多的音訊",
  "跟讀更多的影片",
  "跟讀更多的文章",
  "增加與智慧助手的對話次數",
  "更多增值體驗開發中",
]);
</script>

<style lang="scss" scoped>
.price {
  margin-top: 126px;
  color: #212121;

  .intro {
    flex-basis: 400px;

    .title {
      line-height: 32px;
      font-weight: 600;
    }

    .subtitle {
      font-weight: 400;
      margin-top: 20px;
    }
  }

  .items {
    margin-top: 32px;

    .item {
      display: flex;
      align-items: center;
      line-height: 1;
      gap: 12px;
      font-size: 18px;
      font-weight: 500;
      margin-bottom: 24px;

      &:last-child {
        margin-bottom: 0;
        color: #979797;
      }
    }
  }
}
</style>
