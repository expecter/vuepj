<template>
<div>
    <el-table :data="rows"  border style="width: 100%" v-loading="pageLoading">
    <el-table-column label="1" prop = "0"></el-table-column>
    <el-table-column label="1" prop = "1"></el-table-column>
    <el-table-column label="1" prop = "2"></el-table-column>
    <el-table-column label="1" prop = "3"></el-table-column>
    <el-table-column label="1" prop = "4"></el-table-column>
    <el-table-column label="1" prop = "5"></el-table-column>
    <el-table-column label="1" prop = "6"></el-table-column>
    <el-table-column label="1" prop = "7"></el-table-column>
    <el-table-column label="1" prop = "8"></el-table-column>
    <el-table-column label="1" prop = "9"></el-table-column>
    </el-table>
    <el-button type="primary" @click.native="handleSubmit" >提交</el-button>
</div>
</template>

<script>
let handleSubmit = function () {
  console.log(this.rows)
  this.pageLoading = true
  this.$http.get('https://api.api68.com/pks/getPksHistoryList.do?date=2019-03-21&lotCode=10001')
    .then((res) => {
    //   for (let i in tlData) {
    //     var data = tlData[i]
    //     var strs = data.preDrawCode.split(',')
    //     // this.balls[i] = []
    //     for (let j in strs) {
    //       console.log(i + ' ' + j)
    //       if (this.rows[i]) {
    //         this.rows[i][j] = strs[j]
    //       }
    //     }
    //   }
      this.rows = []
      var tlData = res.data.result.data
      for (let i in tlData) {
        var strs = tlData[i].preDrawCode.split(',')
        var rowData = {}
        for (let j in strs) {
          rowData[j] = strs[j]
        }
        this.rows.push(rowData)
      }
      console.log(this.rows)
      this.pageLoading = false
    })
}
export default {
  name: 'landing-page',
  components: {},
  data () {
    return {
      priod: null,
      pageLoading: false,
      input: '',
      rows: []
    }
  },
  methods: {
    handleSubmit
  }
}
</script>

<style>
</style>
