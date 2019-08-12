<template>
  <div id="app">
    <input type="checkbox" name="TaggedOnly" v-model="taggedOnly" />SDGsに対応するニュースのみ表示する。
    <news-table v-bind:news-data="newsList"></news-table>
  </div>
</template>

<script>
import NewsTable from "./components/NewsTable.vue";

export default {
  name: "app",
  data() {
    return {
      taggedOnly: true,
      newsList: [
        {
          id: 1,
          title: "ULAが5機目となる米空軍の機密通信衛星を打ち上げ",
          url: "https://www.google.com",
          tags: [1, 3, 5, 7, 9, 11, 13, 15, 17],
          date: "2019/08/11 21:45"
        },
        {
          id: 2,
          title:
            "「経験ない暑さ」、オープンウオーターの五輪プレ大会で選手から懸念",
          url: "https://www.google.com",
          tags: [1, 3, 5, 7, 9, 11, 13, 15, 17],
          date: "2019/08/11 21:45"
        },
        {
          id: 3,
          title: "リビア首都攻防戦が3日間停戦に、イスラム教の祭日「犠牲祭」で",
          url: "https://www.google.com",
          tags: [2, 4, 6, 8, 10, 12, 14, 16],
          date: "2019/08/11 21:45"
        }
      ]
    };
  },
  components: {
    NewsTable
  }
};
</script>

<style>
</style>
