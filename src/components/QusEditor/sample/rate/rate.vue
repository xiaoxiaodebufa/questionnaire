<template>
  <div class="sample-item">
    <el-popover placement="right-start" title="量表题" trigger="hover">
      <el-rate v-model="option.answer[0]" :max="option.setting.length" show-text text-color="#ff9900" :texts="texts">
      </el-rate>
      <div class="select-block" slot="reference">
        <i class="el-icon-loading"></i>
        <span>量表题</span>
      </div>
    </el-popover>
  </div>
</template>

<script>
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
  .sample-item{
    width: 125px;
    box-shadow: 0 0 4px 0 #409EFF;
    border-radius: 2px;
    margin: 5px;
    padding: 5px 0;
    cursor:move;
  }
  .select-block {
    margin: 0 10px;
  }
</style>
