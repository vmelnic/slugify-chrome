<template>
    <div class="footer">
        <div class="container">
            <div class="columns">
                <div class="column content">
                    Based on <a href="https://vuejs.org" rel="nofollow">VueJs</a>.<br />
                    CSS framework based on <a href="https://bulma.io" rel="nofollow">Boolma</a>.<br />
                    Web fonts from <a href="http://www.google.com/webfonts" rel="nofollow">Google</a>.
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Footer',
        props: {},
    }
</script>

<style scoped>
    .footer {
        padding-bottom: 3rem;
    }
</style>