<script setup>
import {ref, onMounted} from 'vue'
import { createClient } from '@supabase/supabase-js'

const config = useRuntimeConfig()
const supabase = createClient(config.public.supabaseUrl, config.public.supabaseAnonKey)

let messages = ref([])
let input = ref('')


const channel = supabase.channel('Chats')

async function getMessage(){
    const {data,error} = await supabase.from('Chats').select("message, time")
    console.log(data)
    messages.value = data
    console.log(input)
}


function messageReceived(payload) {
  console.log(payload)
}
// Subscribe to the Channel
channel.on('postgres_changes', {
    schema: 'public',
    event: 'INSERT',
},
(payload) => getMessage()).subscribe()



async function sendMessage(){
    if(input.value){
        const {data,error} = await supabase.from('Chats').insert([{
            message: input.value
        }]);
    }
    input.value=''
}


onMounted(() => getMessage())
</script>


<template>
    <div class="flex flex-col h-[100%] bg-black text-slate-200">
        <!-- Chat Messages Here -->
        <div class="flex w-[100%] min-h-[80vh] p-10 gap-10 flex-wrap justify-evenly">

            <TextCard v-for="items in messages" :time="items.time" :text="items.message"/>
            


        </div>

        <!-- Text Area here -->
        <div class="flex justify-center items-center w-[100%] h-[20vh] p-4 border-t-2 border-t-stone-900 sticky bottom-0 bg-black">
            <div class="flex justify-evenly w-[75%]">
                <UInput class="w-[75%]" size="xl" v-model="input" />
                <UButton class="text-slate-200 cursor-pointer" label="Send" trailing-icon="ic:round-send" size="xl" @click="sendMessage"/>
            </div>
        </div>
    </div>
</template>


<style scoped>

    :root{
        font-family: "Cal Sans", sans-serif;
    }

</style>