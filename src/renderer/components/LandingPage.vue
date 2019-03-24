<template>
<div>
  <el-container>
    <el-table
    :data="balls"
    border
    style="width: 100%">
    <el-table-column
      prop="0"
      label=""
      width="100">
    </el-table-column>
    <el-table-column
      prop="1"
      label=""
      width="50">
    </el-table-column>
    <el-table-column
      prop="2"
      label=""
      width="50">
    </el-table-column>
    <el-table-column
      prop="3"
      label=""
      width="50">
    </el-table-column>
    <el-table-column
      prop="4"
      label=""
      width="50">
    </el-table-column>
    <el-table-column
      prop="5"
      label=""
      width="50">
    </el-table-column>
    <el-table-column
      prop="6"
      label=""
      width="50">
    </el-table-column>
    <el-table-column
      prop="7"
      label=""
      width="50">
    </el-table-column>
    <el-table-column
      prop="8"
      label=""
      width="50">
    </el-table-column>
    <el-table-column
      prop="9"
      label=""
      width="50">
    </el-table-column>
    <el-table-column
      prop="10"
      label=""
      width="50">
    </el-table-column>
    </el-table>
  </el-container>
</div>
</template>

<script>
  export default {
    name: 'landing-page',
    components: {},
    data () {
      return {
        priod: null,
        balls: [ {}, {}, {}, {}, {}, {}, {}, {}, {}, {}, {}, {}, {}, {}, {} ]
      }
    },
    methods: {
      open (link) {
        require('electron').shell.openExternal(link)
      }
    },
    created: function () {
      // this.$http.get('https://www.1396j.com/pk10/getawarddata')
      //   .then((res) => {
      //     var priod = res.data.current.period
      //     // console.log(res.data)
      //     for (var j = 0; j < 15; j++) {
      //       this.balls[j][0] = priod
      //       priod = priod - 1
      //     }
      //   })
      // for (var i = 1; i < 11; i++) {
      //   console.log('AAAAA' + i)
      //   this.$http.post('https://www.1396j.com/pk10/NumbertrendData?ball=' + i + '&count=15')
      //     .then((res) => {
      //       var index = res.url.substr(48, 1)
      //       var index2 = res.url.substr(49, 1)
      //       if (index2 === '0') {
      //         index = 10
      //       }
      //       console.log(index)
      //       // var Tldata = {}
      //       console.log(res)
      //       for (var j = 0; j < 15; j++) {
      //         if (res.data[j]) {
      //           console.log(index + ' ' + res.data[j].number)
      //           this.balls[14 - j][index] = res.data[j].number
      //         }
      //       }
      //       console.log(this.balls)
      //       // this.balls.push(Tldata)
      //     })
      // }
      this.$http.get('https://api.api68.com/pks/getPksHistoryList.do?date=2019-03-21&lotCode=10001')
        .then((res) => {
          // var priod = res.data.current.period
          var tlData = res.data.result.data
          for (let i in tlData) {
            var data = tlData[i]
            var strs = data.preDrawCode.split(',')
            for (let j in strs) {
              console.log(i + ' ' + j)
              if (this.balls[i]) {
                this.balls[i][j] = strs[j]
              }
            }
          }
          console.log(this.balls)
          // for (var j = 0; j < 15; j++) {
          //   this.balls[j][0] = priod
          //   priod = priod - 1
          // }
        })
    }
  }
</script>

<style>
</style>
