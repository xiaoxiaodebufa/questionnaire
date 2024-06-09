<template>
  <div>
    <div class="select-block">
      <el-select :ref="'select'+option.id" v-model="option.answer[0]" placeholder="">
        <el-option v-for="(item,index) in option.setting" :label="item.label" :value="item.value" :key="item.key">
        </el-option>
      </el-select>
    </div>

    <el-collapse-transition>
      <editor v-show="checked" :option="option"></editor>
    </el-collapse-transition>
  </div>
</template>

<script>
  import editor from './editor'
  export default {
    name: 'selector',
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
    watch: {

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
