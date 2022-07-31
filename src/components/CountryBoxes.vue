<template>
    <div class="flex flex-wrap gap-7 my-12">
        <div v-for="(info, i) in countriesInfo" :key="i"
            class="flex-grow shadow max-w-sm w-1/3 bg-blue-100 p-6 rounded flex flex-col">
            <div>
                <h2 class="font-bold text-3xl">{{ info.name }}</h2>
                <p class="text-2xl">Probability: {{parseFloat(info.probability * 100).toFixed(2)}}%</p>
            </div>
            <img class="w-auto" :src="info.img" :alt="info.name + ' flags'">
        </div>
    </div>
</template>
<script>
export default {
    name:"CountryBoxes",
    props: ['countriesInfo'],
}
</script>
