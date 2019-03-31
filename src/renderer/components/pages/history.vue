<template>
<div>
    <el-table :data="rows"  border style="width: 100%" v-loading="pageLoading">
    <el-table-column label="1" prop = "0"></el-table-column>
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
    // var priod = res.data.current.period
    //   var tlData = res.data.result.data
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
      this.rows.push(['Baz11'])
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
