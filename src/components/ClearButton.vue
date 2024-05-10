<template>
    <button @click="clearValues">Limpar</button>
</template>

<script setup>
const props = defineProps({
    clearValues: Function,
})
</script>

<style scoped>
button {
    max-width: 280px;
    width: 100%;
    margin: 1rem auto;
    padding: 5px;
    cursor: pointer;
    background-color: #08f362;
    color: #fff;
    font-size: 1.5rem;
    border-color: transparent;
    transition: all .5s;
    border-radius: 8px;
}

button:hover {
    background-color: #01aa42;
}
</style>