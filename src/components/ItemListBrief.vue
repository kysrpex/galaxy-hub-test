<template>
    <p>
        <g-link class="title" :to="item.link">{{ item.title }}</g-link>
        <span class="tease" v-if="item.tease">
            –
            <span class="markdown" v-html="mdToHtml(item.tease)"></span>
        </span>
    </p>
</template>

<script>
import { mdToHtml } from "~/utils.js";
export default {
    props: {
        item: { type: Object, required: true },
    },
    methods: {
        mdToHtml,
    },
};
</script>

<style scoped>
.title {
    font-weight: bold;
}
.tease {
    font-size: 80%;
}
</style>