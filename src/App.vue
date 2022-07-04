<template>
  <div id="app">
    <div>
      <el-button type="primary" icon="el-icon-search" style="margin-bottom: 2rem;" @click="getList()">筛选心理健康程度较差的</el-button>

    </div>
    <div>
      <el-table :data="tableData" border stripe style="width: 90%;margin: auto;">
        <el-table-column prop="refnm1" label="姓名" width="180">
        </el-table-column>
        <el-table-column prop="refnm2" label="性别" width="180">
        </el-table-column>
        <el-table-column prop="refnm3" label="年龄段" width="180">
        </el-table-column>
        <el-table-column prop="refnm4" label="学历" width="180">
        </el-table-column>
        <el-table-column prop="result1" label="性格取向" width="180">
        </el-table-column>
        <el-table-column prop="result2" label="心理健康程度" width="180">
        </el-table-column>
        <el-table-column prop="result3" label="职业兴趣" width="180">
        </el-table-column>
        <el-table-column prop="result4" label="职业兴趣" width="180">
        </el-table-column>
        <el-table-column prop="result5" label="职业兴趣" width="180">
        </el-table-column>
        <el-table-column prop="result6" label="职业兴趣" width="180">
        </el-table-column>
      </el-table>
    </div>
    
  </div>
</template>

<script>
  import HelloWorld from './components/HelloWorld.vue'

  export default {
    name: 'app',
    components: {
      HelloWorld
    },
    data() {
      return {
        tableData: []
      }
    },
    created() {
      this.getAllList()
      // axios.get('https://tduck-api-new.foxconnedu.com/evaluate/get/sick').then(res=>{
      //     console.log(res,'res')
      //   })
      // https://ques-api.foxconnedu.com/evaluate/get/sic
      // evaluate/get/a7378a8b499b4fbc923334bb0683c518
    },
    methods: {
      getAllList() {
        this.$axios.get('https://ques-api.foxconnedu.com/evaluate/get/a7378a8b499b4fbc923334bb0683c518').then(res => {
          console.log(res, 'res')
          this.tableData = res.data
          console.log(this.tableData, 'table')
        })
      },
      getList(){
        this.$axios.get('https://ques-api.foxconnedu.com/evaluate/get/sick').then(res => {
          console.log(res, 'res')
          this.tableData = res.data
          console.log(this.tableData, 'table1')
        })
      }
    },
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;

  }
  .el-table{
    font-size: 2rem;

  }
  .el-button{
    /* float:right; */
  }
</style>