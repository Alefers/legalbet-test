<template>
    <table class="matches-table">
        <thead>
            <tr>
                <th class="matches-table__th-league">
                    <fragment
                            v-for="(league, lIdx) in match.leagues"
                            :key="lIdx"
                    >
                        <span class="arrow-devider las la-angle-right" v-if="lIdx > 0"></span>
                        <span class="link" :class="getFlagIconClasses(league)">{{league.name}}</span>
                    </fragment>
                </th>
                <th class="matches-table__th">Трансляции</th>
                <th class="matches-table__th">Прогнозы</th>
                <th class="matches-table__th">Хозяева</th>
                <th class="matches-table__th">Ничья</th>
                <th class="matches-table__th">Гости</th>
            </tr>
        </thead>
        <tbody>
            <tr
                    v-for="(game, gIdx) in match.games"
                    :key="gIdx"
            >
                <td class="matches-table__td-match">
                    <div class="matches-comands">
                        <span class="time">{{game.time}}</span>
                        <span class="link">
                            <span>{{game.comand1 + '&nbsp;- '}}</span>
                            <span>{{game.comand2}}</span>
                        </span>
                    </div>

                </td>
                <td class="matches-table__td-broadcast">
                    <div class="matches-broadcast">
                        <div
                                class="broadcast-logo"
                                v-for="(broadcast, bIdx) in game.broadcast"
                                :key="bIdx"
                        >
                            <img class="broadcast-logo__image" :src="'/img/broadcast/' + broadcast + '.png'" :alt="broadcast" />
                        </div>
                    </div>
                </td>
                <td class="matches-table__td">
                    <div v-if="game.forecast" class="forecast-count">
                        {{game.forecast }}
                    </div>
                </td>
                <td class="matches-table__td">
                    <div class="matches-coeff">
                        {{game.coeffs.p1}}
                    </div>
                </td>
                <td class="matches-table__td">
                    <div class="matches-coeff">
                        {{game.coeffs.draw}}
                    </div>
                </td>
                <td class="matches-table__td">
                    <div class="matches-coeff">
                        {{game.coeffs.p2}}
                    </div>
                </td>
            </tr>
        </tbody>
    </table>
</template>

<script>
export default {
    props: {
        match: {
            type: Object,
            default: () => {}
        }
    },
    methods: {
        getFlagIconClasses(league) {
            return league?.flag ? ['link_flag', 'flag-icon', 'flag-' + league.flag] : [];
        }
    }
}
</script>
