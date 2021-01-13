<template>
    <div>
        <h3>Child组件</h3>
        <p>父组件传递过来的值：{{message.name}}</p>
        <button @click="changeMessage">点击 通过改变message 改变父组件msg的值</button>
    </div>
</template>

<script>
    export default {
        name:"Child",
        props:["message"],
        methods:{
            changeMessage(){
                this.message.name="刘能";
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>