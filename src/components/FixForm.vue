<template>
  <div class="main">
    <el-table :data="tableData" border align="left" row-key="id" @header-dragend="moveHeaderSize" >
      <!-- 序号  -->
      <el-table-column  fixed="left" width="60px" label="序号" type="index" class-name="no-drag"></el-table-column>
      <!-- 表头  -->
      <el-table-column v-for="(item, index) in col"  :key="`col_${index}`" :prop="dropCol[index].prop" :label="item.label" :width="dropCol[index].size"></el-table-column>
     <!-- 操作 -->
      <el-table-column fixed="right" class-name="no-drag" label="操作" width="100">
        <template slot-scope="scope">
          <el-button @click="handleClick(scope.row)" type="text" size="small">查看</el-button>
          <el-button type="text" size="small">编辑</el-button>
        </template>
      </el-table-column>
    </el-table>
    <!-- header list -->
    <pre style="text-align: left">
      {{ dropCol }}
    </pre>
    <hr>
    <!-- data list -->
    <pre style="text-align: left">
      {{ tableData }}
    </pre>
  </div>

</template>

<script>

import Sortable from 'sortablejs'

export default {
  data() {
    return {
      refresh: true,
      col: [
        {
          label: '日期',
          prop: 'date',
        },
        {
          label: '姓名',
          prop: 'name',
        },
        {
          label: '地址',
          prop: 'address',
        }
      ],
      dropCol: [
        {
          label: '日期',
          prop: 'date',
          size: 100
        },
        {
          label: '姓名',
          prop: 'name',
          size: 100
        },
        {
          label: '地址',
          prop: 'address',
          size: 500
        }
      ],
      tableData: [
        {
          id: '1',
          date: '2016-05-02',
          name: '王小虎1',
          address: '上海市普陀区金沙江路 100 弄'
        },
        {
          id: '2',
          date: '2016-05-04',
          name: '王小虎2',
          address: '上海市普陀区金沙江路 200 弄'
        },
        {
          id: '3',
          date: '2016-05-01',
          name: '王小虎3',
          address: '上海市普陀区金沙江路 300 弄'
        },
        {
          id: '4',
          date: '2016-05-03',
          name: '王小虎4',
          address: '上海市普陀区金沙江路 400 弄'
        }
      ]
    }
  },
  mounted() {
    this.rowDrop()
    this.colDrag()
  }
  ,
  methods: {
    //行拖拽
    rowDrop() {
      const tbody = document.querySelector('.el-table__body-wrapper tbody')
      const _this = this
      Sortable.create(tbody, {
        onEnd({newIndex, oldIndex}) {
          const currRow = _this.tableData.splice(oldIndex, 1)[0]
          _this.tableData.splice(newIndex, 0, currRow)
        }
      })
    },
    colDrag() {
      // 首先获取需要拖拽的dom节点
      const el1 = document.querySelector('.el-table__header-wrapper tr')
      const _this = this
      Sortable.create(el1, {
        filter: '.no-drag',
        disabled: false, // 是否开启拖拽
        animation: 150, // 拖拽延时，效果更好看
        onEnd: (evt) => {
          const oindex = evt.oldIndex - 1;
          const oldItem = _this.dropCol[oindex]
          _this.dropCol.splice(oindex, 1)
          _this.dropCol.splice(evt.newIndex - 1, 0, oldItem);
        }
      });
    },
    moveHeaderSize(newWidth, oldWidth, column) {
      console.log('newWidth: ', newWidth, ', oldWidth: ', oldWidth)
      this.dropCol.forEach(item => {
        if (column.label === item.label) {
          item.size = newWidth;
        }
      });
    },
  }
}
</script>

<style>
.main {
  margin: 0 auto;
  width: 800px;
}
</style>
