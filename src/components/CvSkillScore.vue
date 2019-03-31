<template>
  <div class="score">
    <span class="label">{{ subject }}</span>
    <span :class="{'is--full': i <= score, square: true }" v-for="i in 5" :key="i"></span>
  </div>
</template>
<script>
export default {
  name: "cv-skill-score",
  props: {
    score: {
      type: Number,
      default: 0
    },
    subject: {
      type: String,
      default: "OpenFrame"
    }
  }
};
</script>
<style lang="scss" scoped>
$color: #4d5357;
$color-dark: darken($color, 10%);
$color-light: lighten($color, 10%);
$size: 0.7em;
.score {
  line-height: 1;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  width: 100%;
}
span.label {
  font-size: 0.8em;
  line-height: 1;
  margin-right: 5px;
}
span.square {
  min-height: $size;
  max-height: $size;
  min-width: $size;
  max-width: $size;
  box-sizing: content-box;
  border: 1px solid lighten($color-light, 35%);
  margin: 0 2px;
  display: inline-block;
  &.is--full {
    background-color: lighten($color-light, 40%);
  }
}
</style>
