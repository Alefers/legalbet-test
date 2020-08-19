<template>
    <section class="container">
        <div class="row">
            <div class="row__col row__col_main">
                <div class="box box_white">
                    <div class="box__header">
                        <Tabs :tabs="tabs" @changetab="goToTab"/>
                    </div>
                    <div class="box__body">
                        <h1>Все матчи</h1>
                    </div>
                </div>
            </div>
            <div class="row__col row__col_aside">
                <div class="box box_gray">

                </div>
            </div>
        </div>
    </section>
</template>

<script>
import Tabs from "../common/Tabs";

export default {
    components: {Tabs},
    data: () => {
        return {
            tabs: [
                {
                    text: 'На сегодня',
                    count: 13,
                    active: false
                },
                {
                    text: 'Все матчи',
                    count: 87,
                    active: true
                },
                {
                    text: 'Составы',
                    active: false
                },
                {
                    text: 'Новости',
                    active: false
                },
                {
                    text: 'Ставки и прогнозы',
                    active: false
                },
            ]
        }
    },
    methods: {
        goToTab(idx) {
            this.tabs = this.tabs.map((tab, index) =>  {
                tab.active = index === idx;
                return tab;
            });
        }
    }
}
</script>
