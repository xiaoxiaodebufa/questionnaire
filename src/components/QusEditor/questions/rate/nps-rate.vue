<template>
  <div>
    <div class="select-block">
      <el-rate v-model="option.answer[0]" :icon-classes="iconClasses" void-icon-class="icon-rate-face-off"
        :colors="colors" :max="option.setting.length" show-text text-color="#ff9900" :texts="texts">
      </el-rate>
    </div>
    <el-collapse-transition>
      <editor v-show="checked" :option="option"></editor>
    </el-collapse-transition>

  </div>
</template>

<script>
  import "../../assets/fonts/style.css"
  import editor from './editor'
  export default {
    name: 'rate',
    components: {
      editor
    },
    props: {
      option: {
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
        value: null,
        colors: {
          4: '#99A9BF',
          9: {
            value: '#F7BA2A',
            excluded: true
          },
          10: '#FF9900'
        },
        iconClasses: {
          4: 'icon-rate-face-1',
          9: {
            value: 'icon-rate-face-2',
            excluded: true
          },
          10: 'icon-rate-face-3'
        } // 等同于 { 2: 'icon-rate-face-1', 4: { value: 'icon-rate-face-2', excluded: true }, 5: 'icon-rate-face-3' }
      }
    },
    computed: {
      texts() {
        let texts = this.option.setting.map(item => {
          return item.label
        })
        return texts
      }
    },
    mounted() {

    },
    methods: {

    }
  }
</script>

<style scoped lang="scss">
  .select-block {
    margin: 0 15px;
  }
</style>