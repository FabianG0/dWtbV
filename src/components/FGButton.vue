<script setup lang="ts">
defineProps({
    textButton: {type: String, default: ''}
})
</script>
<template>
    <div 
        class="flex flex-col w-full text-xl text-center place-content-center p-2 text-black rounded-lg cursor-pointer  border-1 border-solid hover:bg-blue hover:text-white">
            <p> {{ textButton }} </p>
        </div>
</template>