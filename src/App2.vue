<template>
    <div>
        <h3>App组件</h3>
        <p>父组件数据：{{msg}}</p>
        <button @click="changeChild">父组件直接更改子组件数据</button>
        <hr>
        <Child :message="msg"/>
    </div>
</template>

<script>
    import Child from './components/Child';
    export default {
        name:"App",
        components:{Child},
        data(){
            return {
                msg:"赵四"
            }
        },
        methods:{
            changeChild(){
                this.$children[0].myChild="嘻嘻";
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>