<template>
  <teleport to="body">
    <div class="modal">
      <div class="modal__overlay"></div>
      <div class="modal__wrap modal-video">
        <div class="modal__close" @click="closeModal"></div>
        <div class="modal__video">
          <iframe src="https://www.youtube.com/embed/uCNWuSbPnt4?autoplay=1&amp;loop=1&amp;enablejsapi=1&amp;playerapiid=featuredytplayer&amp;controls=0&amp;modestbranding=1&amp;rel=0&amp;showinfo=0&amp;color=white&amp;iv_load_policy=3&amp;theme=light&amp;wmode=transparent&amp;playlist=uCNWuSbPnt4&amp;mute=1" frameborder="0" allow="fullscreen" id="widget2" title="SHOWREEL V2"></iframe>
        </div>
      </div>
    </div>
  </teleport>
</template>

<script>
export default {
  props: {
    type: String,
    default: ''
  },
  methods: {
    closeModal() {
      this.$emit('close', false)
    }
  },
}
</script>

<style lang="scss">
.modal {
  &__wrap {
    &.modal-video {
      max-width: 80%;
      padding: 0;
    }
  }
  &__video {
    position: relative;
    height: 40vw;
    max-width: 100%;
    @media(max-width: 767px) {
      max-width: 100vw;
    }
    iframe {
      position: absolute;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
    }
  }
}
.modal-video {
  .modal {
    &__close {
      &::after, &:before {
        background-color: #fff;
        z-index: 9999;
        height: 2px;
        top: -35px;
      } 
    }
  }
}
</style>