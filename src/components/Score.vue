<template>
    <div>
        <h1>Score App</h1>
        <!-- Saat memakai Directive if,if-else dan else, element yang pakai directive ini literally tidak ditambahkan ke DOM. Artinya memang tidak ada, bukan karena hidden by css -->
        <p v-if="score >= 90">Excelent Score: {{ score }}</p>
        <p v-else-if="score >= 70">Good Score: {{ score }}</p>
        <p v-else-if="score >= 50">Average Score: {{ score }}</p>
        <p v-else>Bad Score: {{ score }}</p>
        <!-- Kalau mau tetap ditambahkan ke DOM, bisa pakai v-show. Ini sebenarnya di balik layar akan di-hidden oleh style css pakai display: none -->
        <p v-show="score >= 90">Show Excelent Score: {{ score }}</p>
    </div>
</template>

<script setup>
import { ref } from "vue";

const score = ref(76);
</script>

<style scoped></style>
