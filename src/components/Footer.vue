<template>
    <footer class="footer">
        <span class="todo-count">
            <span>{{todoNum}}</span>
            <strong v-if="todoNum<=1"> item left</strong>
            <strong v-else> items left</strong>
        </span>
        <ul class="filters">
            <li><a href="#/all" @click="filterTodo('all')" :class="{selected:this.$parent.view==='all'}">All</a></li>
            <li><a href="#/active" @click="filterTodo('active')" :class="{selected:this.$parent.view==='active'}">Active</a></li>
            <li><a href="#/completed" @click="filterTodo('completed')" :class="{selected:this.$parent.view==='completed'}">Completed</a></li>
        </ul>
        <button class="clear-completed" @click="clearCompleted" v-if="filterTodoNum>=1">Clear completed</button>
        <button class="clear-completed" @click="clearCompleted" v-else></button>
    </footer>
</template>

<script>
    export default {
        name:"Footer",
        computed:{
            todoNum(){
                return this.$parent.todoDatas.filter(value=>!value.hasCompleted).length
            },
            filterTodoNum(){
                return this.$parent.todoDatas.filter(value=>value.hasCompleted).length
            }
        },
        methods:{
            filterTodo(childView){
                this.$parent.view=childView;
            },
            clearCompleted(){
                this.$parent.todoDatas=this.$parent.todoDatas.filter(value=>{
                    return !value.hasCompleted
                })
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>