<template>
    <tr>
        <td class="date text-nowrap">{{ article.date }}</td>
        <td class="summary">
            <div v-if="article.external_url" class="title">
                <p class="outlink">
                    <a :href="article.external_url" target="_blank">{{ article.title }}</a>
                </p>
                <div class="link-icon"><a class="fas fa-external-link-alt"></a></div>
                <div class="clearfix"></div>
            </div>
            <g-link v-else :to="article.path" class="title">{{ article.title }}</g-link>
            <p class="tease small">
                {{ article.tease }}
                <template v-if="article.links.length">
                    (<template v-for="(link, index) of article.links">
                        <a :href="link.url" :key="index">{{ link.text }}</a>
                        <template v-if="index < article.links.length - 1">, </template> </template
                    >)
                </template>
            </p>
        </td>
        <td class="location">
            <Continent :continent="article.continent" />
            <template v-if="article.location && article.location.name">
                <a v-if="article.location.url" :href="article.location.url">{{ article.location.name }}</a>
                <template v-else>{{ article.location.name }}</template>
            </template>
        </td>
        <td class="contact">
            <a v-if="article.gtn" href="https://training.galaxyproject.org/">
                <g-image
                    class="gtn-icon"
                    src="/images/galaxy-logos/GTN16.png"
                    alt="Training offered by GTN Member"
                    title="Training offered by GTN Member"
                />
            </a>
            <Contacts :contact="article.contact" :contacts="article.contacts" />
        </td>
    </tr>
</template>

<script>
import Continent from "@/components/Continent";
import Contacts from "@/components/Contacts";
export default {
    components: {
        Continent,
        Contacts,
    },
    props: {
        article: { type: Object, required: true },
    },
};
</script>

<style scoped>
.gtn-icon {
    float: right;
}
td {
    padding-bottom: 1rem;
}
p {
    margin: 0;
}
.outlink {
    float: left;
    width: calc(100% - 15px);
}
.link-icon {
    font-size: 80%;
    float: right;
}
</style>
