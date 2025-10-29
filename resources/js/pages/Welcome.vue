<script setup lang="ts">
import { Head } from '@inertiajs/vue3';
import { AreaChart } from 'lucide-vue-next';
import { Card, CardContent, CardFooter, CardHeader } from '@/components/ui/card';

defineProps<{
    title?: string
    data: {
        name: string
        color: string
        value: any
    }[]
}>()
</script>

<template>
    <Head title="Welcome">

    </Head>
    <div class="flex min-h-screen flex-col items-center bg-[#FDFDFC] p-6 text-[#1b1b18] lg:justify-center lg:p-8 dark:bg-[#0a0a0a]">
        <div class="flex w-full items-center justify-center opacity-100 transition-opacity duration-750 lg:grow starting:opacity-0">
            <main class="flex w-full max-w-[335px] flex-col-reverse overflow-hidden rounded-lg lg:max-w-4xl lg:flex-row">
                <Card>
                    <CardHeader>
                        Заголовок карточки
                    </CardHeader>
                    <CardContent>
                        <AreaChart
                            :data="data"
                            :colors="['blue', 'pink', 'orange', 'red']"
                        />
                    </CardContent>
                    <CardFooter>
                        Подвал карточки
                    </CardFooter>
                </Card>
            </main>
        </div>
    </div>
</template>
