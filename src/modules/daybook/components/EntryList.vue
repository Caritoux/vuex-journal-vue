<template>
    <div class="entry-list-container">
        <div class="px-2 pt-2">
            <input
                type="text"
                class="form-control"
                placeholder="Buscar entrada"
                />
        </div>

        <div class="entry-scrollarea">
            <Entry
                v-for="item in getEntriesbyTerm"
                :key="item"
            />
        </div>
    </div>
</template>

<script>
import { defineAsyncComponent } from 'vue';
import { mapGetters } from 'vuex'

export default {
    components: {
        Entry: defineAsyncComponent(() => import('./Entry.vue'))
    },
    computed: {
        ...mapGetters('journal', ['getEntriesbyTerm'])
    }
}
</script>


<style lang="scss" scoped>
.entry-list-cotainer{
    border-right: 1px solid #2c3e50;
    height: calc( 100vh - 56px );
}

.entry-scrollarea{
    height: calc( 100vh - 110px );
    overflow: scroll;
}
</style>