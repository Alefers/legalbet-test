<template>
    <header class="header">
        <div v-if="screenType === 'mobile'" class="container">
            <div class="header-logo header-logo_cut">
                <img class="header-logo__image" src="img/legalbet-logo.svg" alt="Legalbet logo" />
            </div>
            <div class="main-nav-current-page">{{ activeMenuItem }}</div>
            <div class="hamburger" @click="() => mobileNavOpen = true">
                <i class="las la-bars"></i>
            </div>
        </div>
        <div v-else class="container">
            <div class="header-logo" :class="{ 'header-logo_cut': screenType === 'tablet' }">
                <img class="header-logo__image" src="img/legalbet-logo.svg" alt="Legalbet logo" />
            </div>
            <div class="main-nav-current-page">{{ activeMenuItem }}</div>
            <nav class="desktop-main-nav">
                <main-nav :menu-items="menuItems" :active-item="activeMenuItem" @change="changeMainMenu" />
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
            <div class="hamburger" @click="() => mobileNavOpen = true">
                <i class="las la-bars"></i>
            </div>
        </div>
        <div v-if="screenType === 'mobile' || screenType === 'tablet'" class="mobile-nav" :class="{'mobile-nav_open': mobileNavOpen}">
            <div class="mobile-nav__shadow" @click="closeMobileMenu"></div>
            <div class="mobile-nav__content">
                <div class="mobile-nav__content-inner">
                    <div class="mobile-nav__logo">
                        <div class="header-logo">
                            <img class="header-logo__image" src="img/legalbet-logo.svg" alt="Legalbet logo" />
                        </div>
                    </div>
                    <main-nav :menu-items="menuItems" :active-item="activeMenuItem" @change="changeMainMenu" />
                </div>
            </div>
        </div>
    </header>
</template>

<script>
import MainNav from "./MainNav";
export default {
    components: {MainNav},
    props: {
        screenType: String
    },
    data: () => {
        return {
            mobileNavOpen: false,
            activeMenuItem: 'прогнозы',
            menuItems: ['букмекеры', 'бонусы', 'прогнозы', 'беттинг-центр', 'эксперты', 'блоги', 'база знаний'],
        }
    },
    created() {
        window.addEventListener("resize", this.closeMobileMenu);
    },
    methods: {
        changeMainMenu(item) {
            this.activeMenuItem = item;
            this.closeMobileMenu();
        },
        closeMobileMenu() {
            this.mobileNavOpen = false;
        }
    }
}
</script>
