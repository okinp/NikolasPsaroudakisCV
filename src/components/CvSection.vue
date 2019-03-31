<template>
  <section class="content">
    <h4>{{ sectionData.label }}</h4>
    <ul>
      <li v-for="(entry, eIdx) in sectionData.entries" :key="eIdx">
        <p class="date">{{ entry.date }}</p>
        <div class="detail">
          <div v-if="entry.title">{{ entry.title }}</div>
          <div v-if="entry.organization">{{ entry.organization }}</div>
          <span v-if="entry.extra">{{ entry.extra }}</span>
          <div class="tags" v-if="entry.tags">
            <span class="tag" v-for="(tag, tIdx) in entry.tags" :key="tIdx">
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
  }
}
</script>
<style lang="scss" scoped>
$color: #4d5357;
$color-dark: darken($color, 10%);
$color-light: lighten($color, 10%);
  section.content {
    display: flex;
    flex-direction: column;
    h4 {
      text-transform: uppercase;
      font-size: 0.85em;
      color: $color;
      margin-top: 0;
      margin-bottom: 0.8em;
    }
    ul {
      list-style-type: none;
      padding: 0;
      margin-top: 0.4em;
      li {
        display: flex;
        align-items: flex-start;
        justify-content: flex-start;
        font-size: 0.8em;
        margin-bottom: 0.25em;
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
          > span {
            margin-top: 5px;
            color: $color-light;
            font-size: 0.95em;
          }
        }
      }
    }
  }
.tags {
  display: flex;
  flex-wrap: wrap;
  margin: 6px 0;
  span.tag {
    box-sizing: border-box;
    padding: 1px 2px;
    margin-right: 5px;
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
