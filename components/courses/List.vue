<template lang="pug">
.media-block(v-if="course")
  .media
    img(v-bind:src="course.image[0].url" :alt="course.title")

  .body
    h3.title {{ course.title }}
    p.content {{ course.description }}

    .meta(v-if="showDetail" v-cloak)
      div
        b {{ course.lessons.length | pluralizeLesson }}
      div
        span ・
        | {{ course.difficulty }}
      div.-has-icon(:aria-label="course.duration | time")
        span ・
        i.far.fa-clock
        | {{ course.duration | time }}
</template>

<script>
export default {
  props: ['showDetail', 'course']
}
</script>

<style lang="stylus" scoped>
@import '~assets/css/_variables'

.media
  img
    +tablet-up()
      width: 120px
      height: 120px

.title
  padding-top 0

</style>
