<template>
  <table class="root">
    <thead>
      <tr class="head-tr">
        <th class="col-title">記事のタイトル</th>
        <th class="col-goals">対応するゴール</th>
        <th class="col-date">掲載日時</th>
      </tr>
    </thead>
    <tbody>
      <news-item-tr v-for="item in newsData" v-bind:key="item.id" v-bind="item">{{item.title}}</news-item-tr>
    </tbody>
  </table>
</template>

<script>
import NewsItemTr from "./NewsItemTr.vue";

export default {
  name: "news-table",
  props: ["newsData"],
  components: {
    NewsItemTr
  }
};
</script>

<style lang="scss" scoped>
$mochi_color: rgb(22, 150, 50);

.root {
  border-spacing: 0;

  .head-tr {
    background-color: $mochi_color;
    color: white;

    .col {
      &-title,
      &-goals,
      &-date {
        padding: 8px;
      }

      &-goals {
        width: 11%;
        min-width: 85px;
        max-width: 141px;
      }

      &-date {
        width: 80px;
      }
    }
  }
}
</style>
