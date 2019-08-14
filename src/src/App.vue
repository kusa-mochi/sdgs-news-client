<template>
  <div id="app">
    <input type="checkbox" name="TaggedOnly" v-model="taggedOnly" v-on:change="Reload" />SDGsに対応するニュースのみ表示する。
    <div v-if="loading" class="loader-container">
      <mochi-loader></mochi-loader>
    </div>
    <news-table v-else v-bind:news-data="newsList"></news-table>
  </div>
</template>

<script>
import NewsTable from "./components/NewsTable.vue";
import MochiLoader from "./components/MochiLoader.vue";
import axios from "axios";

export default {
  name: "app",
  data() {
    return {
      taggedOnly: true,
      loading: true,
      newsListUrl: "https://slash-mochi.net/sdgs_news_list/collect_news_async",
      newsList: []
    };
  },
  methods: {
    GetTagList(sdgFlags) {
      let output = [];
      const sdgFlagsArray = sdgFlags.split("");
      for (let iGoal = 1; iGoal <= 17; iGoal++) {
        if (sdgFlagsArray[iGoal - 1] == "1") {
          output.push(iGoal);
        }
      }

      return output;
    },
    Reload() {
      this.loading = true;

      axios.get(this.newsListUrl).then(res => {
        this.newsList = [];
        const nData = res.data.length;
        for (let iData = 0; iData < nData; iData++) {
          // SDGsに対応するニュースのみ表示するモード，かつ，iData番目のニュースがSDGsに対応していない場合
          if (this.taggedOnly && !res.data[iData].sdg_flags.match(/1/))
            continue;

          this.newsList.push({
            date: res.data[iData].date,
            id: res.data[iData].id,
            title: res.data[iData].title,
            url: res.data[iData].link,
            tags: this.GetTagList(res.data[iData].sdg_flags)
          });
        }

        this.loading = false;
      });
    }
  },
  mounted() {
    this.Reload();
  },
  components: {
    NewsTable,
    MochiLoader
  }
};
</script>

<style lang="scss" scoped>
.loader-container {
  width: 100%;
  height: 48px;
  margin-top: 80px;
  margin-bottom: 80px;
  overflow: hidden;

  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: center;
  align-items: flex-start;
}
</style>
