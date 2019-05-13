<template>
    <div>
        我是Two
        <el-row>
            <el-button @click="handleRouter">跳转到One</el-button>
        </el-row>
    </div>
</template>

<script>
    export default {
        methods:{
            handleRouter(){
                this.$router.push('/one')
            }
        },created(){
            //接收路由参数，params方式
            console.log(this.$route.params.id)
        }
    }
</script>

<style scoped>

</style>
