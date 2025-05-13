<script setup>
    const props = defineProps({
        time:{
            type: String
        },

        text: {
            type: String
        }
    })

</script>

<template>
    <UModal :overlay="false">
        <div class="flex flex-col gap-2 h-42 w-70 p-4 bg-zinc-950 border-2 border-zinc-800 shadow-2xl rounded-2xl hover:scale-105 hover:-rotate-1 transition-all duration-300 cursor-pointer">
            <div class="flex justify-end">
                <span>{{time.split('.')[0]}}</span>
            </div>
            <div>
                <p class="text-wrap line-clamp-4">{{text}}</p>    
            </div>
        </div>

        <template #content color="primary">
            <div class="w-70%">
                <div class="p-4">
                    <p class="text-wrap">{{text}}</p>    
                </div>
            </div>
        </template>
    </UModal>
</template>