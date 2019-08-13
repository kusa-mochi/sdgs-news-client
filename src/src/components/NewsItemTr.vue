<template>
  <tr class="news-item-container">
    <td>
      <div class="title-container">
        <div class="title">
          <slot></slot>
        </div>
        <a v-bind:href="url" target="_blank"></a>
      </div>
    </td>
    <td>
      <div class="tag-icon-container">
        <tag-icon
          v-for="tagNumber in tagNumbers"
          v-bind:key="tagNumber.id"
          v-bind:tag-number="tagNumber.number"
        ></tag-icon>
      </div>
    </td>
    <td class="date-container">{{date}}</td>
  </tr>
</template>

<script>
import TagIcon from "./TagIcon.vue";

export default {
  name: "news-item-tr",
  props: ["url", "tags", "date"],
  components: {
    TagIcon
  },
  computed: {
    tagNumbers() {
      let output = [];
      const nTag = this.tags.length;
      for (let iTag = 0; iTag < nTag; iTag++) {
        output.push({
          id: iTag + 1,
          number: this.tags[iTag]
        });
      }

      return output;
    }
  }
};
</script>

<style lang="scss" scoped>
.news-item-container {
  min-height: 72px;

  td {
    position: relative;
    padding: 0;
    border-style: dotted;
    border-color: gray;
    border-width: 0 0 1px 0;
  }

  .title-container {
    width: 100%;
    height: 100%;
    min-height: 2.5em;

    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    justify-content: flex-start;
    align-items: center;

    .title {
      margin: 8px;
    }

    a {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgb(22,150,50);
      opacity: 0;

      &:hover {
        opacity: 0.15;
      }
    }
  }

  .tag-icon-container {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: flex-start;
    align-items: center;
  }

  .date-container {
    height: 40px;
    font-size: 12px;
    text-align: center;
  }
}
</style>