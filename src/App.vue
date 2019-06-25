<template>
    <div id="app">
        <Content/>
        <Footer/>
    </div>
</template>

<script>
    import Content from './components/Content.vue'
    import Footer from "./components/Footer";

    export default {
        name: 'app',
        components: {
            Content,
            Footer
        }
    }
</script>

<style>
    #app {
        font-family: 'Raleway', 'Avenir', Helvetica, Arial, sans-serif;
    }
</style>
