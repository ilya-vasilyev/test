<template>
  <main>
    <p>
      Web development is not the only area of my interest,
      I've done some projects within film and video production industries.
      There was some music composing, sound engineering, filming, directing, editing and animating,
      but mostly <b>motion design and visual effects</b>.
    </p>
    <p>
      And I was always interested in mixing and merging different areas,
      like bringing complex animations into the web or making videos interactive.
    </p>
    <hr>
    <Gallery />
  </main>
</template>

<script>
import Gallery from '@/components/Gallery.vue'

export default {
  name: 'Motion',
  components: {
    Gallery
  },
  metaInfo () {
    return {
      title: 'Ilya Vasilyev | motion designer'
    }
  }
}
</script>

<style>
  .b {
    color: #484;
  }
</style>
