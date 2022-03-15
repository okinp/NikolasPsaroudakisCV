<template>
    <div class="skills-matrix" :style="{ 'page-break-before': 'always' }">
        <h4>{{ dataProp.label }}</h4>
        <div class="skills-matrix__grid">
            <cv-skill-score
                v-for="(entry, idx) in dataProp.entries"
                :key="idx"
                :subject="entry.label"
                :score="entry.score"
            />
        </div>
    </div>
</template>

<script>
import CvSkillScore from "./CvSkillScore";
export default {
    name: "cv-skills-matrix",
    components: {
        CvSkillScore
    },
    props: {
        dataProp: {
            type: Object,
            default: () => ({
                label: "Skills Matrix",
                entries: []
            })
        }
    }
}
</script>
<style lang="scss" scoped>
$color: #4d5357;
$color-dark: darken($color, 10%);
$color-light: lighten($color, 10%);
.skills-matrix {
    display: flex;
    flex-direction: column;
    h4 {
        text-transform: uppercase;
        font-size: 0.85em;
        color: $color;
        margin-top: 0;
        margin-bottom: 0.8em;
    }
}
.skills-matrix__grid {
    display: grid;
    margin: 0 auto;
    align-self: center;
    min-width: 78%;
    max-width: 78%;
    width: 100%;
    grid-template-columns: repeat(4, 1fr);
    grid-gap: 4px;
    margin-top: 0.4em;
    margin-bottom: 1em;
}
</style>
