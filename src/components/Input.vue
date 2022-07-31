<template >
    <p class="font-medium mb-3">Your name is: {{name}}</p>
    <form @submit.prevent="onSubmit">
        <input class="shadow block border w-full p-4 rounded" v-model="name" placeholder="🔍 Enter your name | ex.james">
        <input value="Enter Name" type="submit" class="bg-blue-500 py-3 px-7 
        mt-3 rounded text-white border hover:bg-blue-400 w-full">
    </form>

</template>
<script>
export default {
    name: "Input",
    data() {
        return {
            name: "",
            loading: true
        }
    },
    emits: ["name-from-input", "loading"],
    methods: {
        onSubmit(){
            this.$emit('name-from-input', {name: this.name, loading: this.loading});
        }
    },
}
</script>
