<template>
  <div class="sample-item">
    <el-popover placement="right-start" title="多项选择" trigger="hover">
      <el-checkbox-group v-model="option.answer">
        <el-checkbox v-for="(item,index) in option.setting" :label="item.value"></el-checkbox>
      </el-checkbox-group>
      <div class="select-block" slot="reference">
        <i class="el-icon-loading"></i>
        <span>多项选择</span>
      </div>
    </el-popover>
  </div>
</template>

<script>
  export default {
    name: 'checkbox',
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