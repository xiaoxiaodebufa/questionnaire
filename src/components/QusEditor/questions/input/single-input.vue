<template>
  <div>
    <div class="select-block">
      <el-input v-model="option.answer[0]" :placeholder="option.setting[0].value||'请输入内容'"></el-input>
    </div>
    <el-collapse-transition>
      <editor v-show="checked" :option="option"></editor>
    </el-collapse-transition>

  </div>
</template>

<script>
  import editor from './editor'
  export default {
    name: 'singleInput',
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
