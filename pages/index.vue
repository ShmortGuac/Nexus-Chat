<script setup>

</script>


<template>
    <div class="flex flex-col items-center justify-center h-screen bg-black text-slate-200 border-2 border-slate-300 gap-6">
        <div class="flex flex-col items-center justify-center border-2 border-slate-300">
            <span class="text-8xl">Nexus Chat</span>
            <span>A simple anonymous chat platform</span>
        </div>
        <div class="flex justify-center items-center">
            <div class="button flex items-center justify-center gap-2 text-2xl hover:gap-4 transition-all duration-300 cursor-pointer">
                <a href="/chat">Start Chat</a>
                <Icon name="i-lucide-arrow-right"/>
                <!-- <UButton color="neutral" variant="outline" label="Get Started" trailing-icon="i-lucide-arrow-right" class="text-2xl py-2 px-4"/> -->
            </div>
        </div>
    </div>
</template>


<style scoped>

    span{
        font-family: "Cal Sans", sans-serif;
    }

    .button{
        font-family: "Cal Sans", sans-serif;
    }

</style>