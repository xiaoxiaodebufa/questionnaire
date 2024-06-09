<template>
  <div class="qus-editor">
    <div class="qus-editor-left">
      <div class="sample-list">
        <draggable :list="defalutList" :disabled="disable" :group="ioption" :sort="false" :clone="cloneData">
          <div v-for="(item,index) in defalutList" :key="item.id">
            <sample :qusOption="item"></sample>
          </div>
        </draggable>
      </div>

    </div>

    <div class="qus-editor-right">
      <draggable :list="qusList" :disabled="disable" :group="soption">
        <div class="qus-block" :class="item.id===checkedId?'qus-block-checked':''" v-for="(item,index) in qusList"
          :key="item.id">
          <div class="qus-block-title" @click="changeCheckedId(item)">
            <div class="serial">{{index+1}}.</div>
            <div class="content" v-html="item.title"></div>
          </div>
          <question :qusOption="item" :checked="item.id===checkedId"></question>
        </div>
      </draggable>
    </div>


  </div>

</template>

<script>
  import draggable from 'vuedraggable'
  import question from './questions'
  import sample from './sample'
  import defalutList from './default-question.json'

  export default {
    name: 'QusEditor',
    components: {
      draggable,
      question,
      sample
    },
    props: {
      qusList: {
        type: Array,
        default () {
          return []
        }
      }
    },
    data() {
      return {
        ioption: {
          name: 'qusEditor',
          pull: 'clone'
        },
        soption: {
          name: 'qusEditor',
          pull: 'clone'
        },
        checkedId: '1',
        disable: false,
        defalutList
      }
    },
    methods: {
      changeCheckedId(item) {
        //修改当前选中块，并设置选中时无法排序
        if (this.checkedId === item.id) {
          this.checkedId = null
          this.disable = false
        } else {
          this.checkedId = item.id
          this.disable = true
        }
      },
      cloneData(origin) {
        // clone 从一个数组拖拽到另外一个数组时触发的事件和add不同，clone是复制了数组元素
        // 所以我们可以重新new 拷贝一个新对象
        let data = JSON.parse(JSON.stringify(origin))
        data.id = new Date().getTime() + ''
        return data
      }
    }
  }
</script>

<style scoped lang="scss">
  .qus-editor {
    display: flex;
    flex-flow: row nowrap;
    width: 100%;
  }

  .qus-editor-left {
    width: 25%;
    position: relative;

    .sample-list {
      position: fixed;
      top: 100px;
      left: 300px;
    }
  }

  .qus-editor-right {
    width: 75%;
  }

  .qus-block {
    width: 700px;
    min-height: 100px;
    border: 1px solid #8ad0f5;
    margin: 20px;
    border-radius: 4px;

    &-checked {
      min-height: 200px;
      box-shadow: 0 0 10px 2px #9e9e9e;
    }

    &-title {
      margin-left: 10px;
      display: flex;
      flex-flow: row nowrap;

      .serial {
        margin-block-start: 1em;
        margin-block-end: 1em;
        margin-inline-start: 0px;
        margin-inline-end: 0px;
      }

      .content {
        // width: 650px;
      }
    }
  }

  .qus-block.sortable-ghost {
    background: #55ffff;
  }
</style>