<template>
    <div>
        <form>
            <button v-on:click="increment">Increment {{ counter }}</button>
            <div class="row">
                <label for="firstName">First Name</label>
                <input type="text" id="firstName" name="firstName" placeholder="First Name" />
            </div>
            <br />
            <div class="row">
                <label for="lastName">Last Name</label>
                <input type="text" id="lastName" name="lastName" />
            </div>
            <br />
            <!-- Event modifer -> modifier adalah untuk memodifikasi event handler, contohnya prevent untuk mencegah default behavior dari sebuah event (misalnya submit form). Modifier ini bisa digabungkan, contohnya .prevent.stop untuk mencegah default behavior dan menghentikan event dari menyebar ke elemen lain. -->
            <button v-on:click.prevent="sayHello">Say Hello</button>
        </form>
    </div>
    <h2>Hello {{ getFullName }}</h2>
    <ul>
        <li>
            <h1 :class="['red']">Directive event handling</h1>
        </li>
    </ul>
    <div class="row">
        <label for="firstName">First Name</label>
        <input type="text" id="firstNameEvent" name="firstName" placeholder="First Name" v-on:input="changeFirstName" />
    </div>
    <div class="row">
        <label for="lastName">Last Name</label>
        <input type="text" id="lastNameEvent" name="lastName" v-on:input="changeLastName" />
    </div>
    <br />
    <button v-on:click="counter++">Increment inline {{ counter }}</button>
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

// Event handler -> function yang dipanggil ketika terjadi event, seperti click, input, dll. Event handler akan menerima parameter event yang berisi informasi tentang event yang terjadi, seperti target, type, dll.
function changeFirstName(event) {
    // cara lama:
    // person.firstName = document.getElementById("firstNameEvent").value;
    person.firstName = event.target.value;
}

function changeLastName(event) {
    // cara lama:
    // person.lastName = document.getElementById("lastNameEvent").value;
    person.lastName = event.target.value;
}
</script>

<style scoped>
.row {
    display: flex;
    align-items: center;
    gap: 10px;
}

.red {
    color: red;
}
</style>
