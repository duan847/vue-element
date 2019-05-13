<template>
    <div>
        <el-row :gutter="10">
            <el-col :xs="6" :sm="6" :md="4" :lg="3" :xl="1"><router-link :to="{ name: 'one'}">首页</router-link></el-col>
            <el-col :xs="18" :sm="6" :md="8" :lg="9" :xl="11"><el-input
                    placeholder="搜索 电视剧名/电影名"
                    prefix-icon="el-icon-search">
            </el-input></el-col>
<!--            <el-col :xs="8" :sm="6" :md="4" :lg="3" :xl="1"><div class="grid-content bg-purple-light">4</div></el-col>-->
        </el-row>
    </div>
</template>

<script>
    export default {
        name: "Header"
    }
</script>

<style scoped>

</style>
