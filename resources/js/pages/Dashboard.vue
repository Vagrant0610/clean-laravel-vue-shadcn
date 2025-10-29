<script setup lang="ts">
// Импортируем компонент графика
import VueApexCharts from "vue3-apexcharts";
// Импортируем UI-компоненты
import { Head } from '@inertiajs/vue3';
import { Card, CardAction, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card';
// Импортируем компонент определения цветовой темы
import { useColorMode } from '@vueuse/core';
// Импортируем компонент переключения темы
import ThemeToggle from '@/components/ThemeToggle.vue';

// Данные для графика (ApexCharts)
const chartOptions = {
    chart: { id: 'vuechart-example' },
    xaxis: { categories: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'] },
    theme: { mode: useColorMode().value },
};
const chartSeries = [
    { name: 'series-1', data: [30, 40, 35, 50, 49, 60] }
];

// Данные для простой таблицы
const tableData = [
    { id: 1, name: 'Alice', score: 95 },
    { id: 2, name: 'Bob', score: 88 },
    { id: 3, name: 'Charlie', score: 92 }
];
</script>

<template>
    <div class="p-8">
        <Head title="Dashboard">
            Dashboard
        </Head>
        <Card>
            <CardHeader>
                <CardTitle>Дашборд проекта</CardTitle>
                <CardDescription>Здесь отображаются наши графики и данные.</CardDescription>
                <CardAction><ThemeToggle /></CardAction>
            </CardHeader>
            <CardContent class="space-y-4">
                <!-- График -->
                <div>
                    <h3 class="text-lg font-medium mb-2">Пример графика</h3>
                    <VueApexCharts type="line" height="350" :options="chartOptions" :series="chartSeries"></VueApexCharts>
                </div>

                <!-- Простая таблица -->
                <div>
                    <h3 class="text-lg font-medium mb-2">Пример таблицы</h3>
                    <div class="border rounded-lg">
                        <table class="w-full text-sm">
                            <thead>
                            <tr class="border-b bg-muted/50">
                                <th class="h-12 px-4 text-left">ID</th>
                                <th class="h-12 px-4 text-left">Name</th>
                                <th class="h-12 px-4 text-left">Score</th>
                            </tr>
                            </thead>
                            <tbody>
                            <tr v-for="item in tableData" :key="item.id" class="border-b">
                                <td class="p-4">{{ item.id }}</td>
                                <td class="p-4">{{ item.name }}</td>
                                <td class="p-4">{{ item.score }}</td>
                            </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </CardContent>
        </Card>
    </div>
</template>
