<template>
  <div class="page">
    <header>
      <p class="name">
        Nikolas
        <br />Psaroudakis
      </p>
      <p />
      <ul class="contact">
        <li>www.nikolaspsaroudakis.com</li>
        <li>psaroudakis@gmail.com</li>
        <li>(+30) 6945297001</li>
      </ul>
    </header>
    <cv-section :sectionData="cvdata.sections[1]" />
    <cv-section :sectionData="cvdata.sections[0]" />
    <cv-skills-matrix :dataProp="cvdata.skills" class="breakProper" />
    <cv-section :sectionData="cvdata.sections[2]" class="breakProper" />
    <cv-section :sectionData="cvdata.sections[3]" class="breakProper" />
  </div>
</template>

<script>
import cvdata from "../assets/cv.json";
import CvSection from "./CvSection.vue";
import CvSkillsMatrix from "./CvSkillsMatrix.vue";
export default {
  name: "page",
  components: {
    CvSection,
    CvSkillsMatrix
  },
  data() {
    return {
      cvdata: cvdata
    };
  }
};
</script>
<style lang="scss">
.breakProper {
  page-break-before: auto;
  page-break-after: auto;
  page-break-inside: avoid;
}

.breakBefore {
  page-break-before: always;
  page-break-after: auto;
  page-break-inside: avoid;
}
</style>
<style lang="scss" scoped>
$color: #4d5357;
$color-dark: darken($color, 10%);
$color-light: lighten($color, 10%);

* {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  color: #4d5357;
}

body {
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
  background-color: #fafafa;
  font: 18px "Ubuntu";
  color: $color;
}

.page {
  width: 210mm;
  min-height: 297mm;
  padding: 10mm;
  margin: 10mm auto;
  border: 1px #d3d3d3 solid;
  border-radius: 3px;
  background: white;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
  // -webkit-box-decoration-break: clone;
  header {
    display: flex;
    justify-content: space-between;
    margin-bottom: 3em;
    color: $color;
    p.name {
      text-transform: uppercase;
      // font-family: "Roboto";
      font-weight: 800;
      font-size: 1em;
      line-height: 0.9em;
      margin: 0;
    }
    ul {
      margin: 0;
      list-style-type: none;
      color: $color-light;
      font-size: 0.7em;
    }
  }
}

@page {
  size: A4;
  padding: 0 10mm;
  margin-top: 5em;
}
@page :first {
  margin-top: 0;
}
@media print {
  html,
  body {
    width: 210mm;
    height: 297mm;
  }
  .page {
    border: initial;
    border-radius: initial;
    width: initial;
    min-height: initial;
    box-shadow: initial;
    background: initial;
    break-after: avoid;
  }
}
</style>
