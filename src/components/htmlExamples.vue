<template>
  <div class="flex col-flow">
    <div class="wrapper">
      <div class="flex slides-wrapper">
        <div v-viewer="options" class="images clearfix" style="display: none">
          <template>
            <img v-for="image in images" :src="image.source" :key="image.key" width="250px" height="auto">
          </template>
        </div>
      </div>
      <div class="navbar">
        <button @click="prev">prev</button>
        <button @click="next">next</button>
      </div>
    </div>
  </div>
</template>

<script>
//  script
// import quebraCabeca from './jigsaw.vue'
import 'viewerjs/dist/viewer.css'
import Viewer from 'v-viewer'
import Vue from 'vue'
Vue.use(Viewer, {
  debug: true,
  defaultOptions: {
    zIndex: 9999
  }
})

const sourceImages = []
for (let i = 0; i < 10; i++) {
  sourceImages.push({
    key: 'imagem ' + (i + 1),
    source: require('@/components/images/' + (i + 1) + '.jpg')
  })
}

export default {
  data () {
    return {
      images: [...sourceImages],
      options: {
        toolbar: false,
        inline: true,
        backdrop: false,
        button: false,
        navbar: false,
        title: false,
        keyboard: true,
        minHeight: 450,
        minWidth: 450,
        url: 'data-source',
        movable: false,
        container: '#viewer-container'
      }
    }
  },
  methods: {
    next () {
      const vuer = this.$el.querySelector('.images').$viewer
      vuer.next([true])
    },
    prev () {
      const vuer = this.$el.querySelector('.images').$viewer
      vuer.prev([true])
    }
  }
}
</script>

<style>
.slides-wrapper{
  min-height: 450px;
  min-width: 450px;
}

</style>
