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
</template>
