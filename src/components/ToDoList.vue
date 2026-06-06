<template>
    <div>
        <h1>ToDo List</h1>
        <!-- For Array -->
        <ul>
            <li v-for="item in items">
                {{ item.text }}
            </li>
        </ul>
    </div>
    <!-- For object juga bisa -->
    <h2>Object</h2>
    <div>
        <!-- v-bind:key. Berfungsi supaya saat list diubah atau ditambah item baru, vue tidak akan mereplace seluruh item dari awal, tetapi hanya item yang terkait saja. Best for performance, usahakan selalu pakai v-bind:key -->
        <!-- :key ditempatkan pada elemen yang memiliki v-for. Jika v-for ada di <ul>, maka :key juga di <ul> -->
        <ul v-for="item in items" v-bind:key="item.id">
            <li v-for="(value, key) in item" v-bind:key="key">
                {{ key }}: {{ value }}
            </li>
        </ul>
    </div>
    <h2>List for Range</h2>
    <div v-for="value in 10">Number {{ value }}</div>
    <h2>Gabungan v-for dan v-if</h2>
    <!-- Ini contoh yang perlu hati-hati. v-if itu lebih utama dibandingkan v-for. Kode di bawah akan error akrena item.failed itu tidak ada, karena dia belum dilakukan perulangan. Solusinya v-for dipindah ke parent element, seperti div/template. Rekomendasi pakai template biar tidak ada noise DOM -->
    <!-- ! <ul v-for="item in items" v-bind:key="item.id" v-if="!item.failed"> -->
    <template v-for="item in items" v-bind:key="item.id">
        <ul v-if="!item.failed">
            <li v-for="(value, key) in item" v-bind:key="key">
                {{ key }}: {{ value }}
            </li>
        </ul>
    </template>
</template>

<script setup>
const items = [
    {
        id: 1,
        text: "Learn Vue.js",
        failed: true,
    },
    {
        id: 2,
        text: "Build a ToDo List App",
        failed: false,
    },
    {
        id: 3,
        text: "Master Vue.js",
        failed: false,
    },
];
</script>

<style scoped></style>
