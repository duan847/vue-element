<template>
  <div id="app">
    <el-container ref="homePage">
      <el-header>
        <Header/>
      </el-header>
      <el-main>
        <router-view></router-view>
      </el-main>
    </el-container>


  </div>
</template>

<script>
    import Header from './Header'
    export default {
        components: {
            Header
        },
        data(){
            return {

                clientHeight:'',
            }
        },
        mounted(){
            // 获取浏览器可视区域高度
            this.clientHeight =   `${document.documentElement.clientHeight}`
            //document.body.clientWidth;
            //console.log(self.clientHeight);
            window.onresize = function temp() {
                this.clientHeight = `${document.documentElement.clientHeight}`;
            };
        },
        watch: {
            // 如果 `clientHeight` 发生改变，这个函数就会运行
            clientHeight: function () {
                this.changeFixed(this.clientHeight)
            }
        },

        methods:{

            changeFixed(clientHeight){ //动态修改样式
                // console.log(clientHeight);
                // console.log(this.$refs.homePage.$el.style.height);
                this.$refs.homePage.$el.style.height = clientHeight-20+'px';
            },
        }
    }
</script>

<style>
  .el-header, .el-footer {
    /*background-color: #B3C0D1;*/
    color: #333;
    text-align: center;
    line-height: 60px;
  }

  .el-aside {
    background-color: #D3DCE6;
    color: #333;
    text-align: center;
    line-height: 200px;
  }

  body > .el-container {
    margin-bottom: 40px;
  }

  .el-container:nth-child(5) .el-aside,
  .el-container:nth-child(6) .el-aside {
    line-height: 260px;
  }

  .el-container:nth-child(7) .el-aside {
    line-height: 320px;
  }
</style>
