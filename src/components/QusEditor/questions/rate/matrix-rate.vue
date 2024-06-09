<template>
  <div>
    <div class="select-block">
      <el-table ref="dragTable" class="block-center" :data="option.answer" row-key="id" border fit size="mini"
        highlight-current-row>
        <el-table-column align="center" label="评分">
          <template slot-scope="{row,$index}">
            {{row[0]}}
          </template>
        </el-table-column>

        <el-table-column v-for="(item,index) in option.Xsetting" align="center" :label="item.label">
          <template slot-scope="{row,$index}">
            <el-radio v-model="row[index+1]" :label="item.num" @change="radioChange(row,index+1)">{{''}}</el-radio>
          </template>
        </el-table-column>
      </el-table>

    </div>

    <el-collapse-transition>
      <matrix-editor v-show="checked" :option="option"></matrix-editor>
    </el-collapse-transition>

  </div>
</template>

<script>
  // import {
  //   option
  // } from 'runjs'
  import matrixEditor from './matrix-editor'
  export default {
    name: 'matrixRate',
    components: {
      matrixEditor
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
      'option.Xsetting': {
        deep: true,
        immediate: true,
        handler: function(newValue, oldValue) {
          let cols = this.option.Xsetting.length + 1
          let rows = this.option.Ysetting.length
          this.option.answer = Array.from(Array(rows), () => new Array(cols));
          this.option.answer.forEach((item, index) => {
            item[0] = this.option.Ysetting[index].value
          })
        }
      },
      'option.Ysetting': {
        deep: true,
        immediate: true,
        handler: function(newValue, oldValue) {
          let cols = this.option.Xsetting.length + 1
          let rows = this.option.Ysetting.length
          this.option.answer = Array.from(Array(rows), () => new Array(cols));
          this.option.answer.forEach((item, index) => {
            item[0] = this.option.Ysetting[index].value
          })
        }
      }
    },
    mounted() {

    },
    methods: {
      radioChange(row, index) {
        for (let i = 1; i < row.length; i++) {
          if (i != index) {
            this.$set(row,i,null)
          }
        }
      }
    }
  }
</script>

<style scoped lang="scss">
  .select-block {
    margin: 0 15px;
  }

  .block-center {
    width: 680px;
    margin: 0px auto 20px auto;
  }

</style>
<style type="text/css">
  .el-radio__label {
    padding-left: 0;
  }
</style>
