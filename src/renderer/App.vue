<template>  
  <el-container>
    
    <el-aside width="200px"></el-aside>
    <el-main>
      <div id="app">    
        <landing-page></landing-page>
        <!-- <div>
        <ul>
          <li v-for="item in links"><a @click="$goRoute(item.route)">{{item.text}}</a></li>
        </ul>
        <router-view></router-view>
      </div> -->
      </div>
    </el-main>
  </el-container>
</template>

<script>
  // import LandingPage from '@/components/LandingPage/historyView'
  import LandingPage from '@/components/pages/history'

  export default {
    name: 'electronui',
    components: {
      LandingPage
    },
    data () {
      return {
        links: [
          {
            text: '胡萝卜',
            route: '/home'
          },
          {
            text: '大白菜',
            route: '/page01'
          },
          {
            text: '水蜜桃',
            route: '/page02'
          }
        ]
      }
    }
  }
</script>

<style>
  /* CSS */
</style>
