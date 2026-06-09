<template>
  <div
    class="comments mt-[64px] md:mt-[96px] pb-[32px] md:pb-[64px] lg:mt-[128px]"
  >
    <div class="container m-auto">
      <div class="top py-[32px] md:py-[64px] text-center">
        <div class="hint text-[13px] md:text-[14px]">Comment</div>
        <div class="title text-[24px] md:text-[32px]">使用者評價</div>
      </div>
    </div>

    <div class="items-container">
      <div class="items">
        <div
          v-for="(item, index) in [...comments, ...comments]"
          :key="index"
          class="item"
        >
          <img class="quote" src="/portal-static/icon/double-quote.svg" />

          <div class="top">
            <span>
              <img
                width="56"
                height="56"
                class="rounded-full"
                :src="item.avatar"
              />
            </span>

            <div class="ml-3">
              <div class="name">{{ item.name }}</div>
              <div class="hint">{{ item.hint }}</div>
            </div>
          </div>
          <div class="content" :style="{ width: item.width + 'px' || 'auto' }">
            {{ item.text }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name: "Comments",
};
</script>

<script lang="ts" setup>
import { request } from "@/utils/http";

const items = ref([
  {
    width: 420,
    mixinId: 39491012,
    avatar: "/portal-static/images/avatar.png",
    name: "劉巖^Box定投踐行群7年踐碟",
    hint: "專注訓練",
    text: "Enjoy 使用非常方便，之前是自己寫中文文稿，Enjoy 翻譯成英文，再逐句話的跟著學發音和語音語調，直到95分以上，開始按照正確的語音背誦，現在是每天朗讀背誦笑來老師整理的英語俚語，慣用語，積攢了好多不熟悉的用法，每天都能學到新東西，每天都有進步，真的感覺充實，感謝笑來老師，讓大家一起走在正確的道路上",
  },
  {
    mixinId: 39279749,
    avatar: "/portal-static/images/avatar.png",
    name: "龍小方aytc93",
    hint: "專注訓練",
    text: "每天早上5點起床之後，會先用enjoy進行朗讀。常用成語特別好，每天讀10個，每個有3條語音；語音評估很好用，幫助看出哪個音節需要修正；把1000h上面的手冊用enjoy翻譯出來，生成語音，一次性準備好一個月的內容，這個文字鼓勵我達成每天3小時。",
  },
  {
    width: 420,
    mixinId: 37339898,
    avatar: "/portal-static/images/avatar.png",
    name: "Yvonne",
    hint: "專注訓練",
    text: "這些天真實的感受是，練了就是有效果。好多以前完全注意不到的發音細節，都被靈敏識別並且標註出來了。這些天已經產生很大的變化了，在一系列喉舌唇齒的細小動作調整之後，現在得分比剛練的時候障礙小了太多。之前讀了多少遍根本數不過來，單是系統記錄到的評估次數一天都有四五百遍，但現在，9-10個句子，只用了兩百多遍，就能拿到很多99-100這樣不錯的成績了。特別提示：一定要特別特別重視評估結果裡的顏色標記，及時地被糾正，這幫助太大了。功能裡的“句子分析”太強大，直接拆清楚每個句子裡的所有成分，對於理解語意、朗讀斷句、輕重緩急的拿捏，都提供了非常強大的支援。夥伴們加油！",
  },
  {
    mixinId: 37306363,
    avatar: "/portal-static/images/avatar.png",
    name: "京煥",
    hint: "專注訓練",
    text: "Enjoy 太強大了！我們一家在韓國生活，孩子們的母語自然是韓語，驚訝於 Enjoy竟然支援韓文語法註釋翻譯！年初決定帶著5年級的老大用 Enjoy練習英語後，果斷把課外英語補習班停掉。經過半年的練習，孩子的進步非常明顯，在班裡英語成績一直最好，口語更是不像話得好。更何況很多同學們花錢在英語補習班學習。",
  },
  {
    mixinId: 1054922,
    avatar: "/portal-static/images/avatar.png",
    name: "侯亮",
    hint: "專注訓練",
    text: "Enjoy 非常好用，它對於我最重要的功能是無限拆分任務，幾乎把學英語降低到0，就像小孩子學說話一樣簡單，最後只剩一個字”練“。如果沒學好就是自己練得不夠多。感謝Enjoy的開發團隊，Enjoy讓我欲罷不能。",
  },
  {
    mixinId: 39637034,
    avatar: "/portal-static/images/avatar.png",
    name: "BigGang",
    hint: "專注訓練",
    text: "Enjoy 讓我們家學習英語口語變得像吃飯一樣自然。我和兩個孩子用 Enjoy 每天覆述小豬佩奇一集，孩子三個月下來口語突飛猛進，孩子幼兒園畢業外教英語老師給了極高的評價。我相信隨著我們練習的時間逐漸積累，可能三年或更短時間孩子的英語將完全解鎖。Enjoy 是每一位想學習練習英語的神器，非常推薦。",
  },
  {
    mixinId: 37381381,
    avatar: "/portal-static/images/avatar.png",
    name: "楊秀程",
    hint: "專注訓練",
    text: "Enjoy 是我的健腦房，在每一個發音動作從笨拙到熟練的過程中，我感到很開心。",
  },
  {
    mixinId: 31766,
    avatar: "/portal-static/avatars/31766.jpg",
    name: "阿信",
    hint: "專注訓練",
    text: "發現自己發音錯誤很有幫助，之前是不知不覺，現在注意到了，開始糾正練習。",
  },
  {
    mixinId: 39503702,
    avatar: "/portal-static/avatars/39503702.jpg",
    name: "二十初仲夏的樹",
    hint: "專注訓練",
    text: "五個月，語感和口語熟練度提高了很多，附帶著閱讀能力也提高了，感覺讀多了以後大膽了很多，估計碰到外國人敢開口了，有時候甚至自己都能小小造句了。",
  },
  {
    mixinId: 37300002,
    avatar: "/portal-static/avatars/37300002.jpg",
    name: "黃明英",
    hint: "專注訓練",
    text: "跟著朗讀，慢慢有停頓、升調降調感覺。",
  },
  {
    mixinId: 39440639,
    avatar: "/portal-static/avatars/39440639.jpg",
    name: "朱國慶",
    hint: "專注訓練",
    text: "App 幫助我解決發音問題，就像一位私人教練，隨時糾正發音錯誤，很多舊的發音習慣得到了糾正，讓我的英語發音比之前有了很大的提高。 ",
  },
  {
    mixinId: 40303463,
    avatar: "/portal-static/images/avatar.png",
    name: "東心木",
    hint: "專注訓練",
    text: "朗讀更流利了，表達更地道了。",
  },
  {
    avatar: "/portal-static/images/avatar.png",
    name: "匿名使用者",
    hint: "-",
    text: "在英語方面，提升了發音質量，同時提高了背誦速度及效果；在學習方面，養成了一定的學習習慣，同時也迫使自己不斷的輸出。",
  },
  {
    avatar: "/portal-static/images/avatar.png",
    name: "匿名使用者",
    hint: "-",
    text: "跟著讀了這些天，對學英語不再有恐懼感了，彷彿沒有讀不了的句子了，有這個軟體，英語的學習計劃也直接提前了。",
  },
  {
    avatar: "/portal-static/images/avatar.png",
    name: "匿名使用者",
    hint: "-",
    text: "糾正發音、方便跟讀、瞭解讀音的輕重緩急。",
  },
  {
    avatar: "/portal-static/images/avatar.png",
    name: "匿名使用者",
    hint: "-",
    text: "糾正了很多過去讀錯，混淆的音。翻譯超快，有語音可以跟讀練習真是太好用了！學到了很多自己沒想到過的表達方式，還有很多新詞。記錄自己的練習，也讓自身很有成就感，不再擔心學英語有什麼用，練起來，這個過程就足夠有用了！",
  },
  {
    avatar: "/portal-static/images/avatar.png",
    name: "匿名使用者",
    hint: "-",
    text: "自動音標生成、逐句跟讀功能讓練習很方便，快捷鍵也很好用，口語水平提高了不少。",
  },
]);

const infos = ref<any[]>([]);

const comments = computed(() => {
  return items.value.map((item) => {
    const info = infos.value.find((info) => info.mixinId === item.mixinId);

    if (!info) return item;

    const sumHours = Number(info.recordings_duration) / 1000 / 60 / 60;

    return {
      ...item,
      name: info.name,
      avatar: info.avatar_url || "/portal-static/images/avatar.png",
      hint: `專注訓練 ${sumHours.toFixed(1)} 小時`,
    };
  });
});

onMounted(async () => {
  requestUserInfo();
});

async function requestUserInfo() {
  infos.value = await Promise.all(
    items.value
      .filter((item) => item.mixinId)
      .map(async (item) => {
        const resp = await request(
          `https://enjoy.bot/api/users/${item.mixinId}/stats`
        );

        return { ...resp, mixinId: item.mixinId };
      })
  );
}
</script>
<style lang="scss" scoped>
.comments {
  background: linear-gradient(180deg, #e6f0f9 0%, #fff 100%);
  background-repeat: no-repeat;
  background-size: cover;

  > .container .top {
    .title {
      font-weight: 600;
      color: #3e5c77;
    }

    .hint {
      font-family: "New York";
      font-style: italic;
      font-weight: 400;
      opacity: 0.5;
      color: #3e5c77;
    }
  }

  .items-container {
    overflow: hidden;
    padding: 0 24px;
  }

  .items {
    display: flex;
    flex-wrap: nowrap;
    gap: 16px;
    animation: scroll 90s linear infinite;

    &:hover {
      animation-play-state: paused;
    }

    .item {
      padding: 24px;
      border-radius: 4px;
      background: #fff;
      flex: 0 0 340px;
      position: relative;

      .quote {
        position: absolute;
        right: 24px;
        top: 32px;
        width: 24px;
      }

      .top {
        display: flex;
        align-items: center;

        .name {
          font-size: 16px;
          font-weight: 500;
        }

        .hint {
          font-size: 12px;
          font-weight: 400;
          opacity: 0.6;
          margin-top: 6px;
        }
      }

      .content {
        margin-top: 30px;
        font-weight: 400;
        line-height: 150%;
      }
    }
  }
}

@keyframes scroll {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(-6309px);
  }
}
</style>
