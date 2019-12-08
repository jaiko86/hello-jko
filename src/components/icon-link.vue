<template>
  <a v-if="!underConstruction" :href="link" target="_blank">
    <img :src="imageSrc" :alt="imageAlt" />
  </a>
  <app-tooltip 
    v-else 
    :message="tooltipMessage"
    trigger-display-style="inline-block"
  >
    <template v-slot:tooltip-trigger>
      <img :src="imageSrc" :alt="imageAlt" :class="{disabled: underConstruction}"/>
    </template>
  </app-tooltip>
</template>

<script>
import AppTooltip from './app-tooltip.vue'
import githubIcon from '../assets/icons/github.png'
import codesandboxIcon from '../assets/icons/codesandbox.png'

const map = {
  'github' : {
    src: githubIcon,
    alt: 'GitHub icon',
  },
  'codesandbox' : {
    src: codesandboxIcon,
    alt: 'CodeSandBox icon',
  },
}

export default {
  name: 'IconLink',
  props: {
    link: {
      type: String,
      required: false,
      validator: url => /^http(s)?/.test(url)
    },
    icon: {
      type: String,
      required: true,
      validator: icon => Object.keys(map).includes(icon)
    },
    underConstruction: {
      type: Boolean,
      required: false,
      default: false,
    },
  },
  components: {
    AppTooltip,
  },
  computed: {
    imageSrc() {
      return map[this.icon].src
    },
    imageAlt() {
      return map[this.icon].alt
    },
    tooltipMessage() {
      switch(this.icon) {
        case 'github' :
          return 'I\'m in the process of migrating repositories'
        case 'codesandbox' :
          return 'Demo on CodeSandBox is coming soon'
        default :
          return ''
      }
    },
  },
}
</script>

<style lang="scss" scoped>
img {
  height: 20px;
  &.disabled {
    filter: opacity(0.4);
  }
}
</style>