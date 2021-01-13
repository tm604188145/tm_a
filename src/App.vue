<template>
    <section class="todoapp">
        <header class="header">
            <h1>Todos</h1>
            <input type="text" class="new-todo" placeholder="What need to be done!" v-model="newTodo" @keyup.enter="addTodo">
        </header>
        <section class="main">
            <input type="checkbox" class="toggle-all" id="toggle-all" v-model="isAll">
            <label for="toggle-all"></label>
            <ul class="todo-list">
                <Item v-for="(todo,index) in filterTodoDatas" :index="index" :key="todo.id" :todo="todo"/>
            </ul>
        </section>
        <Footer />
    </section>
</template>

<script>
    import Item from './components/Item'
    import Footer from './components/Footer'
    export default {
        name:"App",
        components:{Item,Footer},
        data(){
            return {
                todoDatas:[],
                newTodo:"",
                view:"all"
            }
        },
        methods:{
            addTodo(){
                if(this.newTodo==="") return;
                let todo={};
                todo.id=new Date().getTime();
                todo.value=this.newTodo;
                todo.hasCompleted=false;
                this.todoDatas.push(todo);
                this.newTodo=""
            }
        },
        computed:{
            isAll:{
                get(){
                    return this.$children.todoNum==0;
                },
                set(value){
                    this.todoDatas.map(todo=>{
                        todo.hasCompleted=value;
                        return todo
                    })
                }
            },
            filterTodoDatas(){
                switch(this.view){
                    case "all":
                        return this.todoDatas;
                    case "active":
                        return this.todoDatas.filter(value=>{
                            return !value.hasCompleted;
                        });
                    case "completed":
                        return this.todoDatas.filter(value=>{
                            return value.hasCompleted;
                        });
                    default:
                        return this.todoDatas;
                }
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>