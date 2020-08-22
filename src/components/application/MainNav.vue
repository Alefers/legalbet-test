<template>
    <ul class="main-nav">
        <li
                class="main-nav__item"
                :class="{'main-nav__item_active': item === activeItem }"
                v-for="(item, idx) in menuItems"
                :key="idx"
                @click="$emit('change', item)"
        >
            {{ item }}
        </li>
    </ul>
</template>

<script>
export default {
    props: {
        activeItem: String,
        menuItems: {
            type: Array,
            default: () => []
        }
    }
}
</script>
