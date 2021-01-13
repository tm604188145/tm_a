<template>
    <div>
        <h3>Child组件</h3>
        <p>父组件传给子组件的数据：{{message}}</p>
        <p>子组件数据：{{myChild}}</p>
        <button @click="changeMessage">点击 通过改变message 改变父组件msg</button>
    </div>
</template>

<script>
    export default {
        name:"Child",
        props:["message"],
        data(){
            return {
                myChild:"哈哈"
            }
        },
        methods:{
            changeMessage(){
                this.$parent.msg="刘能"
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>