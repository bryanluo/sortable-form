<template>
  <div class="main">
    <el-table :data="tableData"
              border
              align="left"
              row-key="id">
      <!--    draggable   -->
      <draggable v-model="col" draggable="true" @end="onEnd">
          <el-table-column v-for="(item, index) in col" :key="`col_${index}`" :prop="item.prop" :label="item.label"/>
      </draggable>
    </el-table>
    <!--    dropCol    -->
    <pre style="text-align: left">
      {{ dropCol }}
    </pre>
    <hr>
    <!--  tableData  -->
    <pre style="text-align: left">
      {{ tableData }}
    </pre>
  </div>

</template>

<script>

import draggable from 'vuedraggable'

export default {
  components: {
    draggable
  },
  data() {
    return {
      col: [
        {
          label: '日期',
          prop: 'date'
        },
        {
          label: '姓名',
          prop: 'name'
        },
        {
          label: '地址',
          prop: 'address'
        }
      ],
      dropCol: [
        {
          label: '日期',
          prop: 'date'
        },
        {
          label: '姓名',
          prop: 'name'
        },
        {
          label: '地址',
          prop: 'address'
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
  created() {
    this.$nextTick(() => {
      this.drag()
    })
  }
  ,
  methods: {
    onEnd(){

    }
    // ending
  }
}
</script>

<style>
.main {
  margin: 0 auto;
  width: 800px;
}
</style>
