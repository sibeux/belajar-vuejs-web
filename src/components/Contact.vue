<script setup>
import { reactive } from 'vue';

const contact = reactive({
    name: "",
    email: "",
    age: 0,
    type: "Regular",
    complain: false,
    message: ""
})
</script>

<template>
    <h1>Contact Us</h1>
    <form>
        <div>
            <label for="name">Name
                <input type="text" id="name" v-model="contact.name">
            </label>
        </div>
        <div>
            <label for="email">Email
                <input type="email" id="email" v-model="contact.email">
            </label>
        </div>
        <div>
            <label for="age">Age
                <input type="number" id="age" v-model.number="contact.age">
            </label>
        </div>
        <div>
            <label for="type">Type
                <select id="type" v-model="contact.type">
                    <option value="Regular">Regular</option>
                    <option value="Premium">Premium</option>
                    <option value="Gold">Gold</option>
                </select>
            </label>
        </div>
        <div>
            <label for="complain">
                <input type="checkbox" id="complain" v-model.boolean="contact.complain">
            </label>
        </div>
        <div>
            <label for="message">Message
                <textarea id="message" v-model="contact.message" cols="30" rows="10"></textarea>
            </label>
        </div>
    </form>
    <hr />
    <h1>Preview</h1>
    <div>
        <h2>Preview Content</h2>
        <p>Name: {{ contact.name }}</p>
        <p>Email: {{ contact.email }}</p>
        <p>Age: {{ contact.age }}</p>
        <p>Type: {{ contact.type }}</p>
        <p>Complain: {{ contact.complain }}</p>
        <p>Message: {{ contact.message }}</p>
    </div>
</template>

<style scoped>

</style>