<template>
    <div class="header">
        <nav class="main-nav">
            <ul>
                <li v-for="(item, idx) in menuItems" :key="idx" v-html="item" />
            </ul>
        </nav>
    </div>
</template>

<script>
export default {
    data: () => {
        return {
            menuItems: ['букмекеры', 'бонусы', 'прогнозы', 'беттинг-центр', 'эксперты', 'блоги', 'база знаний'],

        }
    }
}
</script>
