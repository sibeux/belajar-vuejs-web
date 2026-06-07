<template>
   <div>
      <label for="productId">
         Product Id:
         <select name="" id="" v-model="productId">
            <option value=""></option>
            <option value="product1">Product 1</option>
            <option value="product2">Product 2</option>
            <option value="product3">Product 3</option>
         </select>
      </label>
   </div>

   <div v-if="product">
      <h1>
         {{ product.name }}
      </h1>
      <p>Product ID: {{ product.id }}</p>
      <p>Price: Rp {{ product.price }}</p>
      <p>Stock: {{ product.stock }}</p>
   </div>
</template>

<script setup>
import { onWatcherCleanup, ref, watch, watchEffect } from "vue";

const productId = ref("product1");
const product = ref(null);

// watch(
//    productId,
//    async (newVal, oldVal) => {
//       // Watch ini default-nya lazy, artinya dia hanya dipanggil kalau ada data yang berubah, dalam hal ini productId. Mirip 'ever' di flutter.
//       console.log("call watch callback");
//       if (newVal) {
//          const response = await fetch(`${newVal}.json`);
//          product.value = await response.json();
//       } else {
//          product.value = null;
//       }
//    },
//    {
//       // buat ngeset data pas pertama kali component dirender, meskipun gak ada data yang berubah. Cocok kayak fetch init album di cybeat.
//       immediate: true,
//       // buat jalanin watch callback cuma sekali, waktu pertama kali component dirender. Setelah itu gak akan dipanggil meski ada perubahan data.
//       // once: true,
//    },
// );

// Alternatif cara di atas yang lebih singkat, pakai watchEffect -> gabungan dari watch biasa + data apa yang di-watch + immediate: true
watchEffect(async (newVal, oldVal) => {
   // onWatcherCleanup mirip onUnmounted, tapi ini khusus buat cleanup di dalam watchEffect/watch. Dia akan jalan pas komponen mau di-unmount ATAU pas watcher mau jalan lagi karena ada data baru yang berubah (tapi sebelum watcher yang baru jalan). Karena dia bukan async, maka dia harus ditaruh sebelum await, apabila berada di async watchEffect/watch.
   onWatcherCleanup(() => {
      console.log("run onWatcherCleanup");
   });

   console.log("call watchEffect");
   const response = await fetch(`${productId.value}.json`);
   product.value = await response.json();
});
</script>

<style scoped></style>
