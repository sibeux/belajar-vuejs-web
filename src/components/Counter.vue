<script setup>
import { ref } from "vue";

let count = 0;
let countReactive = ref(0);
let countObjectReactive = ref({
   count: 0,
   name: "sibe",
});

function increment() {
   // untuk non reactive, kita harus mengupdate DOM secara manual ketika nilai count berubah.
   console.info(`Incrementing count: ${count}`);
   count++;
   document.getElementById("count").innerText = `counter : ${count}`;

   // untuk reactive, kita tidak perlu mengupdate DOM secara manual, karena Vue akan mengupdate DOM secara otomatis ketika nilai countReactive berubah.
   console.info(`Incrementing count: ${countReactive.value}`);
   countReactive.value++;

   countObjectReactive.value.count += 100;
   countObjectReactive.value = {
      ...countObjectReactive.value,
      count: countObjectReactive.value.count / 2,
      name: `sibe ${countObjectReactive.value.count}`,
   };
}
</script>

<template>
   <div>
      <h1 id="count">counter : {{ count }}</h1>
      <!-- Tidak perlu .value lagi -->
      <h1 id="count">counter reactive : {{ countReactive }}</h1>
      <h1 id="count">
         counter object reactive : {{ countObjectReactive.count }}
      </h1>
      <h1 id="count">
         counter object reactive : {{ countObjectReactive.name }}
      </h1>
      <button v-on:click="increment">Increment</button>
   </div>
</template>

<style scoped></style>
