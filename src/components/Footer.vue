<template>
    <div class="footer">
        <div class="container">
            <div class="columns">
                <div class="column content">
                    Based on <a v-on:click.prevent="openTab(`https://vuejs.org`)" href="https://vuejs.org" rel="nofollow">VueJs</a>.<br />
                    CSS framework based on <a v-on:click.prevent="openTab(`https://bulma.io`)" href="https://bulma.io" rel="nofollow">Boolma</a>.<br />
                    Web fonts from <a v-on:click.prevent="openTab(`http://www.google.com/webfonts`)" href="http://www.google.com/webfonts" rel="nofollow">Google</a>.
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Footer',
        props: {},
        methods: {
            openTab: function (link) {
                /* eslint-disable */
                chrome.tabs.create({"url": link});
                /* eslint-enable */
            },
        }
    }
</script>

<style scoped>
    .footer {
        padding-bottom: 3rem;
    }
</style>