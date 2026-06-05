<template>
    <div>
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
    <h1>Hello {{ person.firstName }} {{ person.lastName }}</h1>
</template>

<script setup>
import { reactive } from "vue";

const person = reactive({
    firstName: "",
    lastName: "",
});

function sayHello() {
    person.firstName = document.getElementById("firstName").value;
    person.lastName = document.getElementById("lastName").value;
}
</script>

<style scoped>
.row {
    display: flex;
    align-items: center;
    gap: 10px;
}
</style>
