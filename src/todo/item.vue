<template>
    <div :class="['todo-item',todo.completed ? 'completed' : '']">
        <input class="toggle" type="checkbox" v-model="todo.completed">
        <label>{{todo.content}}</label>
        <button class="des" @click="deletetodo">x</button>
    </div>
</template>

<script>
    export default{
        props: {
            todo: {
                type: Object,
                required: true
            }
        },
        methods: {
            deletetodo() {
                this.$emit('del',this.todo.id)
            }
        }
    }
</script>

<style lang="stylus" scoped>
    .todo-item{
        position: relative;
        width: 100%;
        height: 70px;
        background-color: white;
        font-size: 25px;
        line-height: 70px;
        border-bottom: 1px solid rgba(0,0,0,0.06);
        box-sizing: border-box;
    }
    .toggle{
        text-align: center;
        width: 40px;
        height: 40px;
        position: absolute;
        top: 0;
        bottom: 0;
        margin: auto 0;

    }
    label{
        position: absolute;
        white-space: pre-line;
        word-break: break-all;
        padding: 15px 60px 15px 15px;
        margin-left: 45px;
        display: block;
        line-height: 1.2;
        transition: color 0.4s;
    }
    .completed{
        label{
            color: #d9d9d9;
            text-decoration: line-through;
        }
    }
    .des{
        position: absolute;
        right: 20px;
        top: 25px;
        border: none;
        cursor: pointer;
    }
</style>