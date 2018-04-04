<template>
    <div id="app">
        <div class="cover"></div>
        <Header></Header>
        <todo></todo>
        <Footer></Footer>
    </div>
</template>

<script>
    import Header from './todo/header.vue'
    import Footer from './todo/footer.vue'
    import todo from './todo/todo.vue'
    export default {
        components: {
            Header,Footer,todo
        }
    }
</script>

<style scoped>
    #app, .cover{
        position: absolute;
        left: 0;
        right: 0;
        top: 0;
        bottom: 0;
    }
    .cover{
        background-color: #999;
        opacity: 0.7;
        z-index: -1;
    }
</style>