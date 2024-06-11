<template>
  <div>
    <div class="select-block">
      <div class="input-row" v-for="(item,index) in option.setting">
        <div class="input-row-lable">{{option.setting[index].value}}</div>
        <el-input v-model="option.answer[index]" placeholder="请输入内容"></el-input>
      </div>
    </div>
    <el-collapse-transition>
      <editor v-show="checked" :option="option"></editor>
    </el-collapse-transition>

  </div>
</template>

<script>
  import editor from './editor'
  export default {
    name: 'multipleInput',
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

  .input-row {
    margin-bottom: 10px;
    display: flex;
    flex-flow: row nowrap;
    align-items: flex-end;

    &-lable {
      line-height: 20px;
      white-space: nowrap;
      margin-right: 10px;
    }
  }
</style>