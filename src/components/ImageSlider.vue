<script setup lang="ts">
import { ref } from 'vue'

defineProps<{  }>()

const imgs = [
    "album1.jpg",
    "album2.jpeg",
    "album3.jpg",
    "album4.jpg",
    "album5.jpg",
    "album6.jpg",
    "album7.jpg",
    "album8.jpg",
    "album9.jpg",
    "album10.jpg",
    "album11.jpg",
    "album12.jpg"
];
</script>

<template>

    <div data-ride="carousel" data-interval="500" data-pause="false">
        <div>
            <div v-for="img in imgs" :key="img">
                <img v-bind:src="      '/albums/' + img      " />
            </div>
        </div>
    </div>

</template>

<style scoped>

</style>
