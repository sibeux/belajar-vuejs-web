<script setup>
console.info("Hello from HelloVue.vue")

const hello = "<h1>Hello Vue</h1>";
const classHello = 'hello';
const idHello = 'hello';
const buttonDisabled = false;
const data = {
    id: "hello",
    class: "hello"
}

function helloFunc(){
    return "Hello World";
}
</script>

<template>
    <!-- Directive v-bind digunakan untuk mengisi id atau class secara dinamis -->
    <h1 v-bind:id="idHello" v-bind:class="classHello">{{ hello }}</h1>
    <h1 class="hello">{{ hello }}</h1>
    <h1 class="hello">{{ hello.toUpperCase() }}</h1>
    <h1 class="hello">{{ 10 * 10 }}</h1>
    <h2>{{ helloFunc() }}</h2>
    <div v-bind:class="data.class" v-html="hello"></div>
    <div v-bind="data" v-html="hello"></div>
    <!-- Directive v-html digunakan untuk menampilkan data dalam bentuk html -->
    <div v-html="hello"></div>
    <!-- boolean -->
    <button :disabled="buttonDisabled">Enable button</button>
    <button :disabled="!buttonDisabled">Disable button</button>
</template>

<style scoped>
.hello {
    color: #42b983;
}
</style>