<template>
    <div class="pt-1 flex flex-row gap-2">
        <h3 class="w-full p-2 rounded-lg border border-gray-400 text-xl text-gray-900 bg-yellow-50">{{ msg }}</h3>
        <button @click="$emit('delete')" class="flex-1 px-4 py-2 rounded-lg font-semibold text-md text-white bg-green-600 hover:bg-green-700 focus:ring-2 focus:ring-green-300">Done</button>
    </div>
</template>

<script setup lang="ts">

defineProps({
    msg:{
        type:String,
        required:true,
    }
})
defineEmits({
    delete:null,
})
</script>