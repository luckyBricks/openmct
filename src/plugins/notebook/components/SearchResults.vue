<template>
<div class="c-notebook__search-results">
    <div class="c-notebook__search-results__header">Search Results</div>
    <div class="c-notebook__entries">
        <NotebookEntry v-for="(result, index) in results"
                       :key="index"
                       :domain-object="domainObject"
                       :result="result"
                       :entry="result.entry"
                       :read-only="true"
                       :selected-page="result.page"
                       :selected-section="result.section"
                       @changeSectionPage="changeSectionPage"
                       @updateEntries="updateEntries"
        />
    </div>
</div>
</template>

<script>
import NotebookEntry from './NotebookEntry.vue';

export default {
    components: {
        NotebookEntry
    },
    inject: ['openmct', 'snapshotContainer'],
    props: {
        domainObject: {
            type: Object,
            default() {
                return {};
            }
        },
        results: {
            type: Array,
            default() {
                return [];
            }
        }
    },
    methods: {
        changeSectionPage(data) {
            this.$emit('changeSectionPage', data);
        },
        updateEntries(entries) {
            this.$emit('updateEntries', entries);
        }
    }
};
</script>
