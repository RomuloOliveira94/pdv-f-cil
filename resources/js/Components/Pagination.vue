<template>
    <div v-if="links.length > 3">
        <div class="flex flex-wrap -mb-1">
            <template v-for="(link, key) in links">
                <div
                    v-if="link.url === null"
                    :key="key"
                    class="mb-1 mr-1 px-4 py-3 text-gray-400 text-sm leading-4 border rounded"
                    v-html="link.label"
                />
                <Link
                    v-else
                    :key="`link-${key}`"
                    class="mb-1 mr-1 px-4 py-3 focus:text-primary text-sm leading-4 hover:bg-white border focus:border-primary rounded"
                    :class="{ 'bg-white': link.active }"
                    href="#"
                    @click.prevent="navigate(link.url)"
                    v-html="link.label"
                />
            </template>
        </div>
    </div>
</template>

<script>
import { Link } from "@inertiajs/vue3";

export default {
    components: {
        Link,
    },
    props: {
        links: Array,
    },
    methods: {
        navigate(url) {
            if (url === null) return;
            this.$inertia.visit(url, {
                preserveState: true,
                preserveScroll: true,
            });
        },
    },
};
</script>
