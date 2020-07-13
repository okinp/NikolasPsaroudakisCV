<template>
  <section class="content">
    <h4>{{ sectionData.label }}</h4>
    <ul>
      <li
        v-for="(entry, eIdx) in sectionData.entries"
        :key="eIdx"
        :style="getPageBreaks(entry)"
      >
        <p class="date">{{ entry.date }}</p>
        <div class="detail">
          <div class="detail__title" v-if="entry.title">{{ entry.title }}</div>
          <div v-if="entry.organization">{{ entry.organization }}</div>
          <span v-if="entry.extra">{{ entry.extra }}</span>
          <div class="tags" v-if="entry.tags">
            <span
              class="tag"
              v-for="(tag, tIdx) in entry.tags.sort()"
              :key="tIdx"
            >
              {{ tag }}
            </span>
          </div>
        </div>
      </li>
    </ul>
  </section>
</template>
<script>
export default {
  name: "cv-section",
  props: {
    sectionData: {
      type: Object,
      default: () => ({})
    }
  },
  methods: {
    getPageBreaks({ id, type }) {
      const ID = type + "-" + id;
      let style = {
        "page-break-before": "auto",
        "page-break-after": "auto",
        "page-break-inside": "avoid"
      };

      if (ID === "work-1") {
        style = { ...style, "page-break-before": "always" };
      }
      return style;
    }
  }
};
</script>
<style lang="scss" scoped>
$color: #4d5357;
$color-dark: darken($color, 10%);
$color-light: lighten($color, 10%);
section.content {
  display: flex;
  flex-direction: column;
  margin-top: 10px;
  h4 {
    text-transform: uppercase;
    font-size: 0.85em;
    color: $color;
    margin-top: 1rem;
    margin-bottom: 1.8em;
  }
  ul {
    list-style-type: none;
    padding: 0;
    margin-top: 0.2em;
    margin-bottom: 0px;
    li {
      display: flex;
      align-items: flex-start;
      justify-content: flex-start;
      font-size: 0.8em;
      margin-bottom: 10px;
      margin-top: 14px;
      page-break-before: auto;
      page-break-inside: avoid;
      p.date {
        margin: 0;
        text-align: right;
        min-width: 22%;
        max-width: 22%;
      }
      .detail {
        margin-left: 1em;
        min-width: 78%;
        max-width: 78%;
        display: flex;
        flex-direction: column;
        > .detail__title {
          // font-weight: semi-bold;
        }
        > span {
          margin-top: 5px;
          color: $color;
          font-size: 0.95em;
        }
      }
    }
  }
}
.tags {
  display: flex;
  flex-wrap: wrap;
  margin: 7px 0 0 -3px;
  span.tag {
    box-sizing: border-box;
    padding: 1px 2px;
    margin: 3px;
    border-radius: 3px;
    color: $color-dark;
    background-color: lighten($color-light, 50%);
    border: 1px solid lighten($color-light, 42%);
    border-radius: 3px;
    font-size: 10px;
    text-transform: uppercase;
  }
}
</style>
