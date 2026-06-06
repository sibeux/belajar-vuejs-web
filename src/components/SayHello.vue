<template>
    <div>
        <button v-on:click="increment">Increment {{ counter }}</button>
        <div class="row">
            <label for="firstName">First Name</label>
            <input
                type="text"
                id="firstName"
                name="firstName"
                placeholder="First Name"
            />
        </div>
        <br />
        <div class="row">
            <label for="lastName">Last Name</label>
            <input type="text" id="lastName" name="lastName" />
        </div>
        <br />
        <button v-on:click="sayHello">Say Hello</button>
    </div>
    <h1>Hello {{ getFullName }}</h1>
</template>

<script setup>
import { computed, reactive, ref } from "vue";

const counter = ref(0);

function increment() {
    console.log("Incrementing counter");
    counter.value++;
}

const person = reactive({
    firstName: "",
    lastName: "",
});

function sayHello() {
    person.firstName = document.getElementById("firstName").value;
    person.lastName = document.getElementById("lastName").value;
}

// computed => function yang memakai computed akan dijalankan ketika ada perubahan pada data yang dipakai di dalamnya, dan hasilnya akan disimpan dalam cache. Jadi, jika tidak ada perubahan pada data yang dipakai, maka fungsi computed tidak akan dijalankan lagi, dan hasil yang sudah disimpan dalam cache akan digunakan kembali.
const getFullName = computed((oldname) => {
    console.log(`Getting full name: ${person.firstName} ${person.lastName}`);
    console.log(`Old name: ${oldname}`);
    return `${person.firstName} ${person.lastName}`;
});
</script>

<style scoped>
.row {
    display: flex;
    align-items: center;
    gap: 10px;
}
</style>
