<template>
  <component :is="qusOption.type" :option="qusOption" :checked="checked"></component>
</template>

<script>
  import radio from './select/radio'
  import checkbox from './select/checkbox'
  import selector from './select/selector'
  import rate from './rate/rate'
  import singleRate from './rate/single-rate'
  // import multipleRate from './rate/multiple-rate'
  // import matrixRate from './rate/matrix-rate'
  export default {
    name: 'sample',
    components: {
      radio,
      checkbox,
      selector,
      rate,
      singleRate
    },
    props: {
      qusOption: {
        type: Object,
        default () {
          return {}
        }
      },
      checked: {
        type: Boolean,
        default: false
      }
    },
    data() {
      return {
        componentName: '',
        componentData: {}
      }
    },
    created() {
      this.componentName = this.qusOption.type
      this.componentData = this.qusOption
    }
  }
</script>

<style>
</style>
