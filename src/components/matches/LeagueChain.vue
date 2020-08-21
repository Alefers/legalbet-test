<template>
    <div class="league-chain">
        <fragment
                v-for="(league, lIdx) in leagues"
                :key="lIdx"
        >
            <span class="arrow-devider las la-angle-right" v-if="lIdx > 0"></span>
            <span class="link" :class="getFlagIconClasses(league)">{{league.name}}</span>
        </fragment>
    </div>
</template>

<script>
export default {
    props: {
        leagues: {
            type: Array,
            default: () => []
        }
    },
    methods: {
        getFlagIconClasses(league) {
            return league?.flag ? ['link_flag', 'flag-icon', 'flag-' + league.flag] : [];
        }
    }
}
</script>
