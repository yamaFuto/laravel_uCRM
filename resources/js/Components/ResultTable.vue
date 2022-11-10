<script setup>
const props = defineProps({
    'data' : Object
})
</script>

<template>
    <div v-if="data.type === 'perDay' || data.type === 'perMonth' || data.type === 'perYear'" class="lg:w-2/3 w-full mx-auto overflow-auto">
                                    <table class="table-auto w-full text-left whitespace-no-wrap">
                                    <thead>
                                        <tr>
                                            <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100 rounded-tl rounded-bl">
                                                <font style="vertical-align: inherit;">
                                                    <font style="vertical-align: inherit;">年月日</font>
                                                </font>
                                            </th>
                                            <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100">
                                                <font style="vertical-align: inherit;">
                                                    <font style="vertical-align: inherit;">金額</font>
                                                </font>
                                            </th>
                                        </tr>
                                    </thead>
                                    <tbody>
                                        <tr v-for="item in data.data" :key="item.date">
                                            <td class="px-4 py-3">
                                                <font style="vertical-align: inherit;">
                                                    <font style="vertical-align: inherit;">{{item.date}}</font>
                                                </font>
                                            </td>
                                            <td class="px-4 py-3">
                                                <font style="vertical-align: inherit;">
                                                    <font style="vertical-align: inherit;">{{item.total}}</font>
                                                </font>
                                            </td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                            <div v-if="data.type === 'decile'" class="lg:w-2/3 w-full mx-auto overflow-auto">
                                    <table class="table-auto w-full text-left whitespace-no-wrap">
                                    <thead>
                                        <tr>
                                            <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100 rounded-tl rounded-bl">
                                                <font style="vertical-align: inherit;">
                                                    <font style="vertical-align: inherit;">グループ</font>
                                                </font>
                                            </th>
                                            <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100">
                                                <font style="vertical-align: inherit;">
                                                    <font style="vertical-align: inherit;">平均</font>
                                                </font>
                                            </th>
                                            <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100">
                                                <font style="vertical-align: inherit;">
                                                    <font style="vertical-align: inherit;">合計金額</font>
                                                </font>
                                            </th>
                                            <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100">
                                                <font style="vertical-align: inherit;">
                                                    <font style="vertical-align: inherit;">構成比</font>
                                                </font>
                                            </th>
                                        </tr>
                                    </thead>
                                    <tbody>
                                        <tr v-for="item in data.data" :key="item.date">
                                            <td class="px-4 py-3">
                                                <font style="vertical-align: inherit;">
                                                    <font style="vertical-align: inherit;">{{item.decile}}</font>
                                                </font>
                                            </td>
                                            <td class="px-4 py-3">
                                                <font style="vertical-align: inherit;">
                                                    <font style="vertical-align: inherit;">{{item.average}}</font>
                                                </font>
                                            </td>
                                            <td class="px-4 py-3">
                                                <font style="vertical-align: inherit;">
                                                    <font style="vertical-align: inherit;">{{item.totalPerGroup}}</font>
                                                </font>
                                            </td>
                                            <td class="px-4 py-3">
                                                <font style="vertical-align: inherit;">
                                                    <font style="vertical-align: inherit;">{{item.totalRatio}}</font>
                                                </font>
                                            </td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                            <div v-if="data.type === 'rfm'" class="lg:w-2/3 w-full mx-auto overflow-auto">

                            <h2 class="text-center text-2xl my-4">RFM 分析結果</h2>

                            <div class="my-4 text-center">
                                合計: {{data.totals}} 人
                            </div>

                            <h2 class="text-center text-2xl my-4">
                                RFMランクマ毎の人数
                            </h2>

                            <table class="table-auto w-full text-left whitespace-no-wrap">
                                <thead>
                                    <tr>
                                        <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100">Rank</th>
                                        <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100">R</th>
                                        <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100">F</th>
                                        <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100">M</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <tr v-for="rfm in data.eachCount" :key="rfm.rank">
                                        <td class="px-4 py-3">{{rfm.rank}}</td>
                                        <td class="px-4 py-3">{{rfm.r}}</td>
                                        <td class="px-4 py-3">{{rfm.f}}</td>
                                        <td class="px-4 py-3">{{rfm.m}}</td>
                                    </tr>
                                </tbody>
                            </table>

                            <h2 class="text-center text-2xl my-4">
                                RとFの集計表
                            </h2>

                            <table class="table-auto w-full text-left whitespace-no-wrap">
                                <thead>
                                    <tr>
                                        <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100">rRank</th>
                                        <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100">f_5</th>
                                        <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100">f_4</th>
                                        <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100">f_3</th>
                                        <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100">f_2</th>
                                        <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100">f_1</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <tr v-for="rf in data.data" :key="rf.rRank">
                                        <td class="px-4 py-3">{{rf.rRank}}</td>
                                        <td class="px-4 py-3">{{rf.f_5}}</td>
                                        <td class="px-4 py-3">{{rf.f_4}}</td>
                                        <td class="px-4 py-3">{{rf.f_3}}</td>
                                        <td class="px-4 py-3">{{rf.f_2}}</td>
                                        <td class="px-4 py-3">{{rf.f_1}}</td>
                                    </tr>
                                </tbody>
                            </table>
                            </div>
</template>
