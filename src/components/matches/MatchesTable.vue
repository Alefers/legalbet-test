<template>
    <div class="matches-table-wrapper">
        <div v-if="screenType === 'mobile'">
            <league-chain :leagues="match.leagues" />
        </div>
        <table class="matches-table">
            <thead>
                <tr v-if="screenType === 'mobile'">
                    <th class="matches-table__th-league">Матч</th>
                    <th class="matches-table__th">Хозяева</th>
                    <th class="matches-table__th">Ничья</th>
                    <th class="matches-table__th">Гости</th>
                </tr>
                <tr v-else>
                    <th class="matches-table__th-league">
                        <league-chain :leagues="match.leagues" />
                    </th>
                    <th class="matches-table__th">Трансляции</th>
                    <th class="matches-table__th">Прогнозы</th>
                    <th class="matches-table__th">Хозяева</th>
                    <th class="matches-table__th">Ничья</th>
                    <th class="matches-table__th">Гости</th>
                </tr>
            </thead>
            <tbody
                    v-for="(game, gIdx) in match.games"
                    :key="gIdx"
            >
                <tr>
                    <td class="matches-table__td-match">
                        <div class="matches-comands">
                            <span v-if="screenType !== 'mobile'" class="time">{{game.time}}</span>
                            <span class="link">
                                <span>{{game.comand1 + '&nbsp;- '}}</span>
                                <span>{{game.comand2}}</span>
                            </span>
                        </div>
                    </td>
                    <td v-if="screenType !== 'mobile'" class="matches-table__td-broadcast">
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
                    <td v-if="screenType !== 'mobile'" class="matches-table__td">
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
                <fragment v-if="screenType === 'mobile'">
                    <tr
                            v-for="(line, lIdx) in broadcastLines(game.broadcast)"
                            :key="lIdx"
                    >
                        <td class="matches-table__td-match">
                            <div class="matches-comands">
                                <span v-if="lIdx === 0" class="time">{{game.time}}</span>
                            </div>
                        </td>
                        <td class="matches-table__td"
                            v-for="(broadcast, bIdx) in line"
                            :key="bIdx"
                        >
                            <div class="broadcast-logo" v-if="broadcast">
                                <img class="broadcast-logo__image" :src="'/img/broadcast/' + broadcast + '.png'" :alt="broadcast" />
                            </div>
                        </td>
                    </tr>
                </fragment>
            </tbody>
        </table>
    </div>

</template>

<script>
import LeagueChain from "./LeagueChain";

export default {
    components: {LeagueChain},
    props: {
        match: {
            type: Object,
            default: () => {}
        },
        screenType: String
    },
    methods: {
        broadcastLines(broadcast) {
            let lines = [];
            let broadcastCopy = [...broadcast];
            let n = 0;
            do {
                if (n === 0) {
                    lines.push(['', '', '']);
                }
                lines[lines.length - 1][n] = broadcastCopy[0];
                broadcastCopy.shift();
                n++;
                if (n === 3) {
                    n = 0;
                }
            } while (broadcastCopy.length !== 0);
            return lines;
        }
    }
}
</script>
