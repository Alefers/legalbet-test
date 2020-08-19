<template>
    <ul class="tabs">
        <li
                v-for="(tab, idx) in tabs"
                class="tabs__item"
                :class="{'tabs__item_active': tab.active}"
                :key="idx"
                @click="$emit('changetab', idx)"
        >
            {{tab.text}}
            <span class="tabs-item-count" v-if="tab.hasOwnProperty('count') && tab.count !== null" v-html="tab.count" />
        </li>
    </ul>
</template>

<script>
export default {
    props: {
        tabs: {
            type: Array,
            default: () => []
        }
    }
}
</script>
