<template>
    <div class="league-list">
        <h4 class="league-list__heading" v-if="section.type">{{ section.type }}</h4>
        <ul>
            <li
                    v-for="(league, lInd) in section.list"
                    :key="lInd"
                    class="league-list__item"
            >
                <span class="link link_block" :class="getClasses(league)">
                    {{league.name}}
                    <span class="link__count" :class="{'link__count_marked': league.marked}">{{league.count}}</span>
                </span>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props: {
        section: {
            type: Object,
            default: () => {}
        }
    },
    methods: {
        getClasses(league) {
            let classes = league?.flag ? ['link_flag', 'flag-icon', 'flag-' + league.flag] : [];
            if (league.active) {
                classes.push('link_active');
            }
            return classes
        }
    }
}
</script>
