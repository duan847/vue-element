<template>
    <div>
        <el-carousel :interval="5000" arrow="always" :type="carouselType">
            <el-carousel-item v-for="item in 4" :key="item">
                <h3>{{ item }}</h3>
            </el-carousel-item>
        </el-carousel>
        <div>
            <el-row :gutter="10">
                <el-col :xs="12" :sm="8" :md="6" :lg="4" :xl="2" v-for="(o) in 8" :key="o">
                    <el-card :body-style="{ padding: '0px' }">
                        <img src="https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png" class="image">
                        <div>
                            <span>好吃的汉堡</span>
                            <div class="bottom clearfix">
                                <el-button type="text" class="button">操作按钮</el-button>
                            </div>
                        </div>
                    </el-card>
                </el-col>
            </el-row>
        </div>
        我是One
        <el-row>
            <el-button @click='handleRouter'>跳转到Two</el-button>
        </el-row>
    </div>
</template>

<script>
    export default {
        comments:{
        },
        methods:{
            handleRouter(){
                //路由传递参数，params方式，对应的路由标识必须用name，参数不会出现在url
                this.$router.push({name:'two',params:{id:1}})
            }
        },
        data(){
            return {
                // 浏览器可视区域大于768，跑马灯使用卡片模式
                carouselType: ''
            }
        },
        mounted(){
            // 获取浏览器可视区域宽度
            const clientWidth =   `${document.documentElement.clientWidth}`
            if(clientWidth > 768) {
                this.carouselType = 'card'
            }
        },
    }
</script>

<style scoped>
    .el-carousel__item h3 {
        color: #475669;
        font-size: 18px;
        opacity: 0.75;
        line-height: 300px;
        margin: 0;
    }

    .el-carousel__item:nth-child(2n) {
        background-color: #99a9bf;
    }

    .el-carousel__item:nth-child(2n+1) {
        background-color: #d3dce6;
    }



    .bottom {
        margin-top: 13px;
        line-height: 12px;
    }

    .button {
        padding: 0;
        float: right;
    }

    .image {
        width: 100%;
        display: block;
    }

    .clearfix:before,
    .clearfix:after {
        display: table;
        content: "";
    }

    .clearfix:after {
        clear: both
    }
</style>
