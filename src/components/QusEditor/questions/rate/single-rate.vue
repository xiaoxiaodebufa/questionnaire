<template>
  <div>
    <div class="select-block">
      <el-radio-group v-model="option.answer[0]" class="radio-group">
        <el-radio class="radio-group-item" v-for="(item,index) in option.setting" :label="item.value"
          :name="item.label">
          {{item.label}}
          <span class="orange" v-if="!item.notScored"> ({{item.num}}分)</span>
          <span class="orange" v-else="!item.notScored"> (不计分)</span>
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
    name: 'singleRate',
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

  .radio-group {
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