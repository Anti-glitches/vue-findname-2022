<template>
    <div class="text-center w-1/2 m-auto">
        <p class="text-2xl font-bold m-10">{{quotes}}</p>
        <button @click="getQuotes" class="p-4 bg-blue-400 rounded shadow 
        border text-white">Get Cat Quotes</button>
    </div>
    
</template>
<script>
export default {
    name: "About",
    data() {
        return {
            quotes: '',
        }
    },
    methods: {
        async getQuotes(){
            const res = await fetch('https://catfact.ninja/fact');
            const data = await res.json();

            this.quotes = data.fact
        }
    },
    created(){
        this.getQuotes();
    }    
}
</script>