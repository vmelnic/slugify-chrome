<template>
    <div class="section">
        <div class="container">
            <div class="columns is-mobile is-centered">
                <div class="column content has-text-centered">
                    <div class="is-size-1 content" style="color: #ff0087;">slugify</div>
                    <div class="is-size-6 has-text-primary content">
                        generate human-readable slugs from any ordinary string
                    </div>
                    <div class="field has-addons">
                        <div class="control is-expanded">
                            <input class="input" type="text" placeholder="any ordinary string..." v-model="input">
                        </div>
                        <div class="control">
                            <a class="button is-info" v-on:click.prevent="slugify">slugify</a>
                        </div>
                    </div>
                </div>
            </div>
            <div v-if="output" class="columns is-mobile is-centered">
                <div class="column content has-text-centered">
                    <div class="card">
                        <div class="card-content slugify-output">
                            <p class="title" v-on:click.prevent="copy">{{this.output}}</p>
                        </div>
                        <div class="card-footer">
                            <div class="card-footer-item">
                                <a class="button is-light" v-on:click.prevent="copy">copy</a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import Slugify from 'slugify';
    import Copy from 'clipboard-copy';
    import Noty from 'noty';

    export default {
        name: 'Content',
        props: {},
        data: function () {
            return {
                input: null,
                output: null,
                counter: 0,
            }
        },
        created: function () {
            const that = this;
            if (chrome !== 'undefined' && chrome.tabs && chrome.tabs.query) {
                chrome.tabs.query({active: true, currentWindow: true}, function (tabs) {
                    that.input = tabs[0].title;
                });
            }
        },
        methods: {
            slugify: function () {
                if (this.input && this.input.trim().length > 0) {
                    const string = this.input.trim().substring(0, Math.min(this.input.length, 255));
                    this.output = Slugify(string, {replacement: '-', lower: true});
                } else {
                    this.input = null;
                }
            },
            copy: function () {
                if (this.input && this.input.trim().length > 0) {
                    Copy(this.output).then(() => {
                        new Noty({
                            theme: 'sunset',
                            layout: 'topRight',
                            timeout: 3000,
                            type: 'success',
                            text: 'Copied!',
                        }).show();
                    });
                }
            }
        }
    }
</script>

<style scoped>
    @import "../../node_modules/noty/lib/noty.css";
    @import "../../node_modules/noty/lib/themes/sunset.css";

    .field.has-addons {
        margin-top: 20px;
    }

    .slugify-output {
        cursor: pointer;
    }

    .section {
        padding: 1rem;
    }
</style>
