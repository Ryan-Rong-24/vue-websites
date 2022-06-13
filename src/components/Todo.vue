<template>
    <div>
        <label for="new-todo">Add a todo</label>
        <textarea @keyup.enter="addNewTodo" v-model="newTodoText" placeholder="E.g. Feed the Cat" id="new-todo"></textarea>
        <button @click.prevent="addNewTodo">Add</button>
        <ul>
            <TodoItem v-for="(todo,index) in todos" :key="todo.id" :title="todo.title" @remove="todos.splice(index,1)" />
        </ul>

        <button @click.stop="counter+=1">Add 1</button>
        <button @click="counter=0">Clear</button>
        <p>This button has been clicked {{counter}} times</p>
        
    </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";

export default {
    components:{
        TodoItem,
    },
    data:()=>({
        newTodoText: '',
        todos:[
            {
                id:1,
                title: 'Do the dishes',
            },
            {
                id:2,
                title: 'Take out the trash',
            },
            {
                id:3,
                title: 'Mow the lawn',
            },
        ],
        newTodoId:4,
        counter:0,
    }),
    methods:{
        addNewTodo: function(){
            this.todos.push({
                id: this.newTodoId++,
                title: this.newTodoText,
            })
            this.newTodoText = ''

        }
    },
}
</script>