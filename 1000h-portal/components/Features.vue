<template>
  <div class="features mt-[64px] md:mt-[96px] lg:mt-[128px]">
    <div class="container m-auto">
      <div class="top flex justify-between">
        <div class="text-greyscale_1">
          <div class="title text-[20px] md:text-[32px]">特色功能</div>
          <div class="subtitle text-[14px] md:text-[16px]">
            你能想到的，只要是對學習有幫助的功能，我們都實現了。
          </div>
        </div>

        <div class="hint text-greyscale_4">
          Product <br />
          Features
        </div>
      </div>

      <div class="cards grid-cols-1 md:grid-cols-2 lg:grid-cols-4">
        <div v-for="(feature, index) in features" :key="index" class="card">
          <div class="mr-6">
            <span class="icon">
              <img :src="feature.icon" />
            </span>
          </div>

          <div>
            <div class="title">{{ feature.title }}</div>
            <div class="subtitle">{{ feature.subtitle }}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name: "Features",
};
</script>

<script lang="ts" setup>
const features = ref([
  {
    icon: "/portal-static/images/head-phone.png",
    title: "音訊視覺化跟讀",
    subtitle: "匯入的音訊，我們會進行解析，提供視覺化跟讀",
  },
  {
    icon: "/portal-static/images/camera.png",
    title: "影片視覺化跟讀",
    subtitle: "既然音訊可以跟讀，影片當然也可以",
  },
  {
    icon: "/portal-static/images/lang.png",
    title: "文章閱讀",
    subtitle: "匯入各類外語文章，進行解析閱讀",
  },
  {
    icon: "/portal-static/images/robot.png",
    title: "AI 自然對話",
    subtitle: "最稱職的人工智慧外語陪練",
  },
  {
    icon: "/portal-static/images/note.png",
    title: "重溫筆記",
    subtitle: "學習遇到難點？先新增筆記，再鞏固複習",
  },
  {
    icon: "/portal-static/images/book.png",
    title: "詞典助記",
    subtitle: "學習遇到生詞？新增到生詞本，再鞏固複習",
  },
  {
    icon: "/portal-static/images/cham.png",
    title: "社群競賽",
    subtitle: "每日、每週、每月都有人跟你一起學習進步",
  },
]);
</script>

<style lang="scss" scoped>
.features {
  .top {
    .title {
      font-weight: 600;
    }

    .subtitle {
      margin-top: 4px;
      font-weight: 400;
    }

    .hint {
      font-family: "New York";
      font-size: 14px;
      font-style: italic;
      font-weight: 400;
      text-align: right;
    }
  }

  .cards {
    display: grid;
    gap: 48px;
    margin-top: 32px;

    .card {
      display: flex;

      .icon {
        display: inline-block;
        width: 64px;
        height: 64px;
        display: flex;
        align-items: center;
        justify-content: center;
      }

      .title {
        margin-bottom: 16px;
        font-size: 20px;
        font-weight: 500;
      }

      .subtitle {
        color: #979797;
        font-size: 14px;
        font-weight: 400;
      }
    }

    .compitition {
      color: #fff;
      background-image: url("/portal-static/images/bg-features.png");
      background-repeat: no-repeat;
      background-size: cover;
      position: relative;
      overflow: hidden;

      &::after {
        content: "";
        position: absolute;
        top: 48px;
        right: -20px;
        width: 824px;
        height: 448px;
        background-image: url("/portal-static/images/rank.png");
      }
    }
  }
}
</style>
