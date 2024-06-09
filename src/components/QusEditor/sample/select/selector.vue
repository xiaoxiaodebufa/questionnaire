<template>
  <div class="sample-item">
    <el-popover placement="right-start" title="下拉框选择" trigger="hover">
      <el-select :ref="'select'+option.id" v-model="option.answer[0]" placeholder="">
        <el-option v-for="(item,index) in option.setting" :label="item.label" :value="item.value" :key="item.key">
        </el-option>
      </el-select>
      <div class="select-block" slot="reference">
        <i class="el-icon-loading"></i>
        <span>下拉框选择</span>
      </div>
    </el-popover>
  </div>
</template>

<script>
  export default {
    name: 'selector',
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
    watch: {

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
