<template>
    <section class="container">
        <div class="row">
            <div class="row__col row__col_main">
                <div class="box box_white">
                    <div class="box__header">
                        <Tabs :tabs="tabs" @changetab="goToTab"/>
                    </div>
                    <div class="box__body">
                        <h1 class="box-h1">Все матчи</h1>
                        <p>
                            На этой странице представлен весь список предстоящих футбольных и хоккейных матчей в самых
                            популярных турнирах, а также коэффициенты букмекерских контор на основные исходы этих
                            поединков. Кликнув по любому названию матча, вы получите полную информацию о нем: подробное
                            превью, все о составах команд, статистика личных встреч, ставки и прогнозы, а также лучшие
                            коэффициенты букмекерских контор.
                        </p>
                        <h2 class="box-h2">
                            29 марта
                            <span class="box-h2__sub">
                                 сегодня
                            </span>
                        </h2>
                        <h3 class="box-h3">
                            <i class="box-h3__icon las la-futbol"></i>
                            Футбол
                        </h3>

                        <MatchesTable
                                v-for="(match, mIdx) in matches.football"
                                :key="mIdx"
                                :match="match"
                                :screen-type="screenType"
                        />
                    </div>
                    <div class="box__body">
                        <h3 class="box-h3">
                            <i class="box-h3__icon las la-hockey-puck"></i>
                            Хоккей
                        </h3>

                        <MatchesTable
                                v-for="(match, mIdx) in matches.hockey"
                                :key="mIdx"
                                :match="match"
                                :screen-type="screenType"
                        />
                    </div>
                </div>
            </div>
            <div class="row__col row__col_aside">
                <div class="box box_gray">
                    <div class="box__body">
                        <league-list v-for="(league, lInd) in leagues" :key="lInd" :section="league" />
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
import Tabs from "../common/Tabs";
import MatchesTable from "./MatchesTable";
import LeagueList from "./LeagueList";

export default {
    props: {
        screenType: String
    },
    components: {
        LeagueList,
        MatchesTable,
        Tabs
    },
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
            ],
            matches: {
                football: [
                    {
                        leagues: [
                            {
                                name: 'Россия',
                                flag: 'ru',
                            },
                            {
                                name: 'Премьер-лига',
                            },
                        ],
                        games: [
                            {
                                comand1: 'Локомотив',
                                comand2: 'Ницца',
                                broadcast: [
                                    'youtube',
                                    'telesport',
                                ],
                                time: '19:00',
                                forecast: 3,
                                coeffs: {
                                    p1: 2.45,
                                    draw: 2.45,
                                    p2: 2.45
                                }
                            },
                            {
                                comand1: 'Лейпциг',
                                comand2: 'Наполи',
                                broadcast: [
                                    'youtube',
                                    'telesport'
                                ],
                                time: '19:00',
                                coeffs: {
                                    p1: 2.45,
                                    draw: 2.45,
                                    p2: 2.45
                                }
                            },
                        ]
                    },
                    {
                        leagues: [
                            {
                                name: 'ФНЛ'
                            }
                        ],
                        games: [
                            {
                                comand1: 'Локомотив',
                                comand2: 'Ницца',
                                broadcast: [
                                    'youtube',
                                    'telesport',
                                    'match2'
                                ],
                                time: '19:00',
                                forecast: 4,
                                coeffs: {
                                    p1: 2.45,
                                    draw: 2.45,
                                    p2: 2.45
                                }
                            },
                            {
                                comand1: 'Лейпциг',
                                comand2: 'Наполи',
                                broadcast: [
                                    'match2'
                                ],
                                time: '19:00',
                                forecast: 2,
                                coeffs: {
                                    p1: 2.45,
                                    draw: 2.45,
                                    p2: 2.45
                                }
                            },
                        ]
                    },
                    {
                        leagues: [
                            {
                                name: 'ПФЛ',
                                flag: 'ru'
                            }
                        ],
                        games: [
                            {
                                comand1: 'Локомотив',
                                comand2: 'Ницца',
                                broadcast: [
                                    'match2'
                                ],
                                time: '19:00',
                                forecast: 2,
                                coeffs: {
                                    p1: 2.45,
                                    draw: 2.45,
                                    p2: 2.45
                                }
                            },
                            {
                                comand1: 'Лейпциг',
                                comand2: 'Наполи',
                                broadcast: [
                                    'youtube',
                                    'telesport',
                                    'match2'
                                ],
                                time: '19:00',
                                forecast: 2,
                                coeffs: {
                                    p1: 2.45,
                                    draw: 2.45,
                                    p2: 2.45
                                }
                            },
                        ]
                    }
                ],
                hockey: [
                    {
                        leagues: [
                            {
                                name: 'Кубок России',
                                flag: 'ru',
                            }
                        ],
                        games: [
                            {
                                comand1: 'Динамо Киев',
                                comand2: 'АЕК',
                                broadcast: [
                                    'youtube',
                                    'telesport'
                                ],
                                time: '19:00',
                                forecast: 2,
                                coeffs: {
                                    p1: 2.45,
                                    draw: 2.45,
                                    p2: 2.45
                                }
                            }
                        ]
                    },
                ]
            },
            leagues: [
                {
                    list: [
                        { name: 'Все лиги', count: 100, active: true, marked: true}
                    ]
                },
                {
                    type: 'Футбол',
                    list: [
                        { name: 'Премьер-лига', flag: 'ru', count: 4, active: false, marked: false },
                        { name: 'ФНЛ', flag: 'ru', count: 12, active: false, marked: false },
                        { name: 'ПФЛ', flag: 'ru', count: 5, active: false, marked: true },
                        { name: 'Кубок России', flag: 'ru', count: 36, active: false, marked: true },
                        { name: 'Премьер-лига', flag: 'gb-eng', count: 8, active: false, marked: false },
                        { name: 'Чемпионшип', flag: 'gb-eng', count: 0, active: false, marked: false },
                        { name: 'Бундеслига', flag: 'de', count: 0, active: false, marked: false },
                        { name: 'Лига 1', flag: 'fr', count: 1, active: false, marked: false },
                        { name: 'Премьер-лига', flag: 'kz', count: 4, active: false, marked: false },
                        { name: 'Лига чемпионов', flag: 'uefa-cl', count: 12, active: false, marked: true },
                        { name: 'Лига Европы', flag: 'uefa-el', count: 8, active: false, marked: false },
                        { name: 'ЧМ 2018', flag: 'euro-2018', count: 5, active: false, marked: false },
                    ]
                },
                {
                    type: 'Хоккей',
                    list: [
                        { name: 'КХЛ', flag: 'ru', count: 5, active: false, marked: false },
                        { name: 'Олимпийские игры', flag: 'ru', count: 0, active: false, marked: false },
                    ]
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
