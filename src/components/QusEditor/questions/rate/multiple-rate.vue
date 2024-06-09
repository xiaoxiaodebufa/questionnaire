<template>
  <div>
    <div class="select-block">
      <el-checkbox-group class="checkbox-group" v-model="option.answer">
        <el-checkbox class="checkbox-group-item" v-for="(item,index) in option.setting" :label="item.value">
          {{item.label}}
          <span class="orange" v-if="!item.notScored"> ({{item.num}}分)</span>
          <span class="orange" v-else="!item.notScored"> (不计分)</span>
        </el-checkbox>
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
    name: 'multipleRate',
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

  .checkbox-group {
    display: flex;
    flex-flow: column nowrap;

    &-item {
      margin: 8px 0;
    }
  }

  .orange {
    color: #efa030;
  }
</style>
