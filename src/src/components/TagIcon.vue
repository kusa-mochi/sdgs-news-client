<template>
  <div class="icon-container" v-bind:style="containerStyle" v-bind:title="toolTipMessage">
    <div class="icon">{{tagNumber}}</div>
  </div>
</template>

<script>
export default {
  name: "tag-icon",
  props: ["tagNumber"],
  data() {
    return {
      size: 28,
      tagColors: [
        "#E5243B",
        "#DDA63A",
        "#4C9F38",
        "#C5192D",
        "#FF3A21",
        "#26BDE2",
        "#FCC30B",
        "#A21942",
        "#FD6925",
        "#DD1367",
        "#FD9D24",
        "#BF8B2E",
        "#3F7E44",
        "#0A97D9",
        "#56C02B",
        "#00689D",
        "#19486A"
      ],
      toolTips: [
        "貧困をなくそう",
        "飢餓をゼロに",
        "すべての人に健康と福祉を",
        "質の高い教育をみんなに",
        "ジェンダー平等を実現しよう",
        "安全な水とトイレを世界中に",
        "エネルギーをみんなにそしてクリーンに",
        "働きがいも経済成長も",
        "産業と技術革新の基礎をつくろう",
        "人や国の不平等をなくそう",
        "住み続けられるまちづくりを",
        "つくる責任、つかう責任",
        "気候変動に具体的な対策を",
        "海の豊かさを守ろう",
        "陸の豊かさも守ろう",
        "平和と公正をすべての人に",
        "パートナーシップで目標を達成しよう"
      ]
    };
  },
  computed: {
    containerStyle() {
      return {
        width: this.size + "px",
        height: this.size + "px",
        backgroundColor: this.tagColors[this.tagNumber - 1],
        borderRadius: this.size / 2 + "px"
      };
    },
    toolTipMessage() {
      return this.toolTips[this.tagNumber - 1];
    }
  }
};
</script>

<style lang="scss" scoped>
.icon-container {
    font-weight: bold;
    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    justify-content: center;
    align-items: center;

    .icon {
        font-size: 14px;
        color: white;
    }
}
</style>