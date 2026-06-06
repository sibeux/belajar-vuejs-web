<script setup>
import { ref } from "vue";

const array = ["red", "bold"];

const isRed = ref(false);
const isBold = ref(false);

function toggleRed() {
    isRed.value = !isRed.value;
}

function toggleBold() {
    isBold.value = !isBold.value;
}

const style1 = {
    color: "red",
};

const style2 = {
    textTransform: "uppercase",
    fontWeight: "bold",
};
</script>

<template>
    <h1 v-bind:class="{ red: isRed, bold: isBold }">Style</h1>
    <h1 v-bind:class="['red', 'bold']">Style</h1>
    <h1 v-bind:class="array">Style</h1>

    <h1 v-bind:style="style1">Style 1</h1>
    <h1 v-bind:style="style2">Style 2</h1>
    <h1 v-bind:style="[style1, style2]">Style 1 & 2</h1>

    <button v-on:click="toggleRed">Red</button>
    <button v-on:click="toggleBold">Bold</button>
</template>

<!-- scoped artinya nama class css ini hanya berlaku di component/class vue ini saja, tidak akan conflict dengan class vue lain meskipun namanya sama -->
<style scoped>
.red {
    color: red;
}

.bold {
    font-weight: bold;
    text-transform: uppercase;
}
</style>
