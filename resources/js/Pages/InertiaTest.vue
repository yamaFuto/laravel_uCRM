<script setup>
import {Link} from '@inertiajs/inertia-vue3';
import {ref} from 'vue';

const newTitle = ref('')
const newContent = ref('')
</script>

<template>
    <a href="/">a</a><br>
    <Link href="/">Link</Link><br>
    <Link :href="route('inertia.index')">name</Link><br>
    <Link :href="route('inertia.show', { id: 60 })">route</Link>


    <div class="mb-8"></div>
    <input type="text" name="newTitle" v-model="newTitle"><br>
    <input type="text" name="newContent" v-model="newContent"><br>
    <Link as="button" method="post" :href="route('inertia.store')" :data="{
        title: newTitle,
        content: newContent
    }">store</Link>
</template>
