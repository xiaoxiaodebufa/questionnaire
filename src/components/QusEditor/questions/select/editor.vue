<template>
  <div class="editor">
    <span class="editor-span"></span>
    <tinymce v-model="option.title" :height="100" :width="680" class="block-center" />
    <el-table ref="dragTable" class="block-center" :data="option.setting" row-key="id" border fit size="mini"
      highlight-current-row :key="tableKey">
      <el-table-column align="center" label="选项" width="230">
        <template slot-scope="{row,$index}">
          <div style="display: flex;flex-flow: row nowraps;align-items: center;">
            <el-input v-model="row.value"></el-input>
            <svg-icon class="add-or-delete" icon-class="add-circle" @click="addRow($index)" />
            <svg-icon class="add-or-delete" icon-class="minus-circle" @click="deleteRow($index)" />
          </div>
        </template>
      </el-table-column>

      <el-table-column align="center" label="数值">
        <template slot-scope="{row}">
          <span>{{row.label}}</span>
        </template>
      </el-table-column>

      <el-table-column align="center" label="图片" width="120" v-if="option.type!='selector'">
        <template slot-scope="{row}">
          <svg-icon class="drag-handler" icon-class="add-img" />
        </template>
      </el-table-column>

      <el-table-column align="center" label="默认选中" width="80">
        <template slot-scope="{row}">
          <el-checkbox v-model="row.defaultChecked"></el-checkbox>
        </template>
      </el-table-column>

      <el-table-column align="center" label="排序" width="80">
        <template slot-scope="{row,$index}">
          <svg-icon class="drag-handler" icon-class="arrow-up-circle" @click="sortUp($index)" />
          <svg-icon class="drag-handler" icon-class="direction-down-circle" @click="sortDown($index)" />
        </template>
      </el-table-column>

    </el-table>
  </div>
</template>

<script>
  import Tinymce from '@/components/Tinymce'
  export default {
    name: 'editor',
    components: { Tinymce },
    props: {
      option: {
        type: Object,
        default () {
          return {}
        }
      }
    },
    data() {
      return {
        tableKey: Math.random()
      }
    },
    created() {
      // this.$nextTick(() => {
      // 	this.setSort()
      // })
    },
    methods: {
      addRow(index) {
        //新增一条选项 在选中选项下方
        this.option.setting.splice(index + 1, 0, {
          label: `选项`,
          value: `选项`,
          defaultChecked: false
        })
      },
      deleteRow(index) {
        //删除选中选项
        this.option.setting.splice(index, 1)
      },
      sortUp(index) {
        //排序上调一个位置
        if (index > 0) {
          [this.option.setting[index - 1], this.option.setting[index]] = [this.option.setting[index], this.option
            .setting[index - 1]
          ]
          // 更新key重新渲染数据
          this.tableKey = Math.random()
        }
      },
      sortDown(index) {
        //排序下调一个位置
        if (index < this.option.setting.length - 1) {
          [this.option.setting[index], this.option.setting[index + 1]] = [this.option.setting[index + 1], this.option
            .setting[index]
          ]
          // 更新key重新渲染数据
          this.tableKey = Math.random()
        }
      }
    }
  }
</script>
<style scoped lang="scss">
  .editor {
    margin-top: 20px;
    // padding-top: 10px;
    padding-bottom: 20px;
    border-top: 1px solid #dfe4e6;
    position: relative;
    background: #dfe4e6;
  }

  .editor-span {
    width: 0px;
    height: 0px;
    border: 10px solid transparent;

    border-bottom: 10px solid #dfe4e6;
    position: absolute;
    left: 50px;
    top: -20px;
  }

  .drag-handler {
    width: 20px;
    height: 20px;
    cursor: pointer;
  }

  .add-or-delete {
    width: 25px;
    height: 25px;
    margin: auto 5px;
  }

  .block-center {
    width: 680px;
    margin: 20px auto 0 auto;
  }
</style>
