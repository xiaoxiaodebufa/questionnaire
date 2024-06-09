<template>
  <div class="sample-item">
    <el-popover placement="right-start" title="单项选择" trigger="hover">
      <el-radio-group v-model="option.answer[0]">
        <el-radio v-for="(item,index) in option.setting" :label="item.value" :name="item.label">
          {{item.label}}
        </el-radio>
      </el-radio-group>
      <div class="select-block" slot="reference">
        <i class="el-icon-loading"></i>
        <span>单项选择</span>
      </div>
    </el-popover>
  </div>
</template>

<script>
  export default {
    name: 'radio',
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
    mounted() {

    },
    methods: {

    }
  }
</script>

<style scoped lang="scss">
  .sample-item{
    width: 125px;
    border-radius: 2px;
    box-shadow: 0 0 4px 0 #409EFF;
    margin: 5px;
    padding: 5px 0;
    cursor:move;
  }
  .select-block {
    margin: 0 10px;
  }
</style>
