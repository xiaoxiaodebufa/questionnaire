<template>
  <div>
    <div class="select-block">
      <el-radio-group v-model="option.answer[0]">
        <el-radio v-for="(item,index) in option.setting" :label="item.value" :name="item.label">
          {{item.label}}
        </el-radio>
      </el-radio-group>
    </div>

    <el-collapse-transition>
      <editor v-show="checked" :option="option"></editor>
    </el-collapse-transition>
  </div>
</template>

<script>
  import editor from './editor'
  export default {
    name: 'radio',
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
