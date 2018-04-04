<template>
    <section class="mid">
        <input type="text" class="add" autofocus placeholder="接下去要做什么？" @keyup.enter="addTodo">
        <Item :todo="todo" v-for="todo in filtered" :key="todo.id" @del="deleteTodo"></Item>
        <Tabs :filter="filter" :todos="todos" @toggle="toogleFilter" @clearAll="clearAll"></Tabs>
    </section>
</template>

<script>
    import Item from './item.vue'
    import Tabs from './tabs.vue'
    let id=0;
    export default{
        components: {
            Item,Tabs
        },
        data() {
            return {
                todos: [],
                filter: 'all'
            }
        },
        computed:{
            filtered(){
                if(this.filter === 'all'){
                    return this.todos
                }
                const completed = this.filter === 'completed';
                return this.todos.filter(todo => completed === todo.completed)
            }
        },
        methods: {
            addTodo(e) {
                this.todos.unshift({
                    id: id++,
                    content: e.target.value.trim(),
                    completed: false
                })
                e.target.value = ''
            },
            deleteTodo(id){
                this.todos.splice(this.todos.findIndex(todo => todo.id === id),1)
            },
            toogleFilter(state){
                this.filter=state
            },
            clearAll(){
                this.todos = this.todos.filter(todo => !todo.completed)
            }
        }
    }
</script>

<style scoped>
    .mid{
        width: 600px;
        margin: 0 auto;
        box-shadow: 0 0 5px #666;
    }
    .add{
        position: relative;
        width: 100%;
        height: 70px;
        font-size: 25px;
        color: #666;
        padding: 0 20px;
        box-sizing: border-box;
    }
</style>