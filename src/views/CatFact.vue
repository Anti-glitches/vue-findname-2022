<template>
    <div class="text-center w-1/2 mx-auto">
        <h1 class="text-3xl font-bold">Get your Cat FACT</h1>
        <p v-cloak class="text-2xl m-10">"{{quotes}}"</p>
        <button @click="getQuotes" class="p-4 bg-blue-500 rounded shadow 
        border text-white">Get More 🐱</button>
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
            this.quotes = "loading..."

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
<style>

[v-cloack]{
    display: none;
}
[v-cloak] > * { 
    display:none 
}

[v-cloak]::before { 
    content: "loading…" 
}
</style>