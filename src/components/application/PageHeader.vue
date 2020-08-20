<template>
    <header class="header">
        <div class="container">
            <div class="header-logo">
                <img class="header-logo__image" src="img/legalbet-logo.svg" alt="Legalbet logo" />
            </div>
            <nav>
                <ul class="main-nav">
                    <li class="main-nav__item" v-for="(item, idx) in menuItems" :key="idx" v-html="item" />
                </ul>
            </nav>
            <div class="action-panel">
                <div class="action-opener action-opener-support">
                    <i class="action-opener__icon las la-life-ring"></i>
                    Поддержка
                </div>
                <div class="action-opener">
                    <i class="action-opener__icon las la-search"></i>
                    Поиск
                </div>

            </div>
            <div class="unknown-icon">
                FL
            </div>
        </div>
    </header>
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
