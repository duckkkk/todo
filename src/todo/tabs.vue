<template>
    <div class="helper">
        <span class="left">{{unFinished}} items</span>
        <span class="tabs">
            <span :class="[state,filter === state ? 'actived' : '']" v-for="state in states" :key="state" @click="toggleFilter(state)">{{state}}</span>
        </span>
        <span class="clear" @click="clearAll">ClearCompleted</span>
    </div>
</template>

<script>
    export default{
        props:{
          filter: {
              type:String,
              required: true
          },
          todos:{
              type:Array,
              required: true
          }
        },
        data(){
            return{
                states: ['all','active','completed']
            }
        },
        computed:{
          unFinished(){
            return this.todos.filter(todo => !todo.completed).length
          }
        },
        methods: {
            toggleFilter(state) {
                this.$emit('toggle',state)
            },
            clearAll(){
                this.$emit('clearAll')
            }
        }
    }
</script>

<style lang="stylus" scoped>
    .helper{
        display: flex;
        justify-content: space-between;
        padding: 5px 0;
        line-height: 30px;
        background-color: white;
        font-size: 14px;
    }
    .left, .clear, .tabs{
        padding: 0 10px;
        box-sizing: border-box;
    }
    .tabs{
        width: 200px;
        display: flex;
        justify-content: space-around;
        cursor: pointer;
        *{
            display inline-block
            padding 0 10px
            cursor pointer
            border 1px solid rgba(175,47,47,0)
            &.actived{
                border: 1px solid rgba(175,47,47,0.4);
                border-radius: 5px;
            }
        }
    }
    .clear{
        cursor pointer
    }
</style>