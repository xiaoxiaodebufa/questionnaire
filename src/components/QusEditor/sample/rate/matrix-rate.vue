<template>
  <div>
    <div class="select-block">
      <div class="table">
        <div class="row">
          <div class="table-col table-cell-hight"></div>
          <div class="table-row table-cell-hight">
            <div class="table-cell" :style="{'width':100/option.setting.length+'%'}"
              v-for="(item,index) in option.setting">
              {{item.label}}
            </div>
          </div>
        </div>
        <div class="row">
          <div class="table-col table-cell-hight">
            wenzi
          </div>
          <el-radio-group v-model="option.answer[0]" class="table-row table-cell-hight">
            <el-radio class="table-cell" :style="{'width':100/option.setting.length+'%'}"
              v-for="(item,index) in option.setting" :label="item.value" :name="item.label">
              {{''}}
            </el-radio>
          </el-radio-group>
        </div>

      </div>
    </div>

    <editor v-if="checked" :option="option"></editor>
  </div>
</template>

<script>
  import editor from './editor'
  export default {
    name: 'matrixRate',
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

  .table {
    width: 100%;

    .row {
      width: 100%;
      display: flex;
      flex-flow: row nowrap;
    }

    &-col {
      width: 15%;
      text-align: center;
    }

    &-row {
      width: 85%;
      display: flex;
      flex-flow: row nowrap;
      align-items: center;
    }

    &-cell {
      margin-left: 0;
      margin-right: 0;
      text-align: center;
      border: 1px solid #001528;
    }

    &-cell-hight {
      height: 20px;
      margin: 5px 0;
    }
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
<style type="text/css">
  .el-radio__label{
    padding-left: 0;
  }
</style>
