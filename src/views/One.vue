<template>
    <div>
        <el-carousel :interval="5000" arrow="always" :type="carouselType">
            <el-carousel-item v-for="(item,index) in hotList" :key="index">
                <el-image :src="item.cover" layz ></el-image>
                <h3>{{ item.name }}</h3>
            </el-carousel-item>
        </el-carousel>
        <div>
            <el-row :gutter="10">
                <el-col :xs="12" :sm="8" :md="6" :lg="4" :xl="3" v-for="(item,index) in hotList" :key="index" >
                    <router-link :to="{ name: 'two', params: { id: item.id }}">
                    <el-card :body-style="{ padding: '0px' }">
                        <el-image :src="item.cover" ></el-image>
                        <div>
                            <span>{{item.name}}</span>
                        </div>
                    </el-card>
                    </router-link>
                </el-col>
            </el-row>
        </div>
    </div>
</template>

<script>
    import {selectHotPage, selectTopPage} from '@/api/video'
    export default {
        comments:{
        },
        methods:{
            selectHotPage(){
                selectHotPage({size:this.hotSize}).then(resp => {
                    this.hotList = resp.records
                })
            },
            selectTopPage(){
                selectTopPage({size:this.topSize}).then(resp => {
                    this.TopList = resp.records
                })
            }
        },
        data(){
            return {
                // 浏览器可视区域大于768，跑马灯使用卡片模式
                carouselType: '',
                hotSize: 4,
                hotList: null,
                topSize: 12,
                topList: null
            }
        },
        created(){
            //分页查询热播电影
            this.selectHotPage()
            this.selectTopPage()
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
