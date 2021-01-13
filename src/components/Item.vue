<template>
    <li :class="{completed:todo.hasCompleted,editing:editedTodo===todo}">
        <div class="view">
            <input type="checkbox" class="toggle" v-model="todo.hasCompleted">
            <label @dblclick="editTodo(todo)">{{todo.value}}</label>
            <button class="destroy" @click="deleteTodo(todo.id)"></button>
        </div>
        <input type="text" class="edit" v-focus v-model="todo.value" 
        @keyup.enter="doneTodo(todo)" @blur="doneTodo(todo)" @keyup.esc="cannelTodo(index)">
    </li>
</template>

<script>
    export default {
        name:"Item",
        props:["todo","index"],
        data(){
            return {
                editedTodo:"",
                oldValue:""
            }
        },
        methods:{
            deleteTodo(id){
                this.$parent.todoDatas=this.$parent.todoDatas.filter((value)=>{
                    return !(value.id==id);
                })
            },
            editTodo(todo){
                this.oldValue=todo.value;
                this.editedTodo=todo;
            },
            doneTodo(todo){
                this.editedTodo="";
                if(todo.value==""){
                    this.deleteTodo(todo.id);
                }
            },
            cannelTodo(index){
                this.$parent.todoDatas[index].value=this.oldValue;
                this.editedTodo=""
            }
        },
        directives:{
            focus(el){
                // console.log("el",el);
                // console.log("value",value);
                el.focus();
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>