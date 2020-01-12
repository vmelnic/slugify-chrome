<template>
    <div class="footer">
        <div class="container">
            <div class="columns">
                <div class="column content">
                    Based on <a v-on:click.prevent="openTab(`https://vuejs.org`)" href="https://vuejs.org" rel="nofollow">VueJs</a>.<br />
                    CSS framework based on <a v-on:click.prevent="openTab(`https://bulma.io`)" href="https://bulma.io" rel="nofollow">Boolma</a>.<br />
                    Web fonts from <a v-on:click.prevent="openTab(`http://www.google.com/webfonts`)" href="http://www.google.com/webfonts" rel="nofollow">Google</a>.
                    <p class="has-text-grey-light">
                        Version: {{version}}
                    </p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Footer',
        data: function () {
            return {
                version: '1.1.0',
            }
        },
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
        background-color: #fafafa;
        padding: 1rem;
    }
</style>
