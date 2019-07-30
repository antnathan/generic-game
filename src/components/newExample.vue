<template>
  <div class="box col-flow image-viewer">
    <div class="container">
      <figure class="image container">
        <transition-group name="fade">
          <div class="img-wrap" v-for="image in images" :key="image.key" v-show="image.visible">
            <viewer v-if="!disableZoom" :options="viewerOpts">
                <slot name="image">
                    <img :src="image.source">
                </slot>
            </viewer>
          </div>
        </transition-group>
      </figure>
    </div>
    <div class="container">
      <div class="level">
        <div class="level-item">
          <b-button @click="prev">
            <b-icon
                icon="arrow-left">
            </b-icon>
          </b-button>
        </div>
        <div class="level-item">
          <b-button @click="next">
            <b-icon
                icon="arrow-right">
            </b-icon>
          </b-button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
//  script
// import quebraCabeca from './jigsaw.vue'

import Vue from 'vue'
import Buefy from 'buefy'
import 'buefy/dist/buefy.css'
import 'viewerjs/dist/viewer.css'
import Viewer from 'v-viewer'
Vue.use(Viewer)
Vue.use(Buefy)

const sourceImages = []
for (let i = 0; i < 13; i++) {
  sourceImages.push({
    key: 'imagem ' + (i + 1),
    source: require('@/components/images/' + (i + 1) + '.jpg'),
    visible: false
  })
}

export default {
  data () {
    return {
      images: [...sourceImages],
      image: {},
      index: 0,
      viewerOpts: {
        'inline': false,
        'button': false,
        'navbar': false,
        'title': false,
        'toolbar': false,
        'tooltip': false,
        'movable': true,
        'zoomable': true,
        'rotatable': false,
        'scalable': false,
        'transition': true,
        'fullscreen': false,
        'keyboard': false,
        'url': 'data-source'
      }
    }
  },
  created () {
    this.image = this.images[this.index]
    this.image.visible = true
  },
  methods: {
    next () {
      this.image.visible = false
      if (this.index < this.images.length - 1) {
        this.index++
        this.image = this.images[this.index]
      }
      this.image.visible = true
    },
    prev () {
      this.image.visible = false
      if (this.index !== 0) {
        this.index--
        this.image = this.images[this.index]
      }
      this.image.visible = true
    }
  }
}
</script>

<style lang="scss">
.image-viewer{
  .image{
    height: 360px;
    width: 630px;
    position: relative;
    span{
      display: flex;
      justify-content: center;
      &::after{
        background: linear-gradient(to right, rgba(0,0,0,0) 0%,rgba(0,0,0,0) 45%,rgba(0,0,0,0.4) 50%,rgba(0,0,0,0) 100%);
        content: "";
        height: 100%;
        width: 2em;
        position: absolute;
      }
    }
    .img-wrap{
      position: absolute;
      img{
        height: 360px;
        width: auto;
      }
    }
  }
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
