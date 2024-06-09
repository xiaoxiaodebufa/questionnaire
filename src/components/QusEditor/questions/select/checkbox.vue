<template>
  <div>
    <div class="select-block">
      <el-checkbox-group v-model="option.answer">
        <el-checkbox v-for="(item,index) in option.setting" :label="item.value"></el-checkbox>
      </el-checkbox-group>
    </div>

    <el-collapse-transition>
      <editor v-show="checked" :option="option"></editor>
    </el-collapse-transition>
  </div>
</template>

<script>
  import editor from './editor'
  export default {
    name: 'checkbox',
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