<script setup lang="ts">
import FGButton from '@/components/FGButton.vue';
import {ref} from 'vue'
const URL_AUDIO = 'https://us-tuna-sounds-files.voicemod.net/1a274ea7-318c-4884-9528-13d7bb83c3f4-1662344895710.mp3'
const isOpenQuestion = ref(false)
const isNotResponse = ref(true)
const sizeReject = ref(100)
const heightReject = ref(4)
const backAudio = ref(new Audio(URL_AUDIO))
const textRespose = ['Si', 'Ya entendi la broma, ahora selecciona este', 'Parece que lo estas pensando', 'Claramente esta la opcion correcta', 'Si ya lo pensaste ahora si', 'Presiona aqui para decir que si','Estoy esperando tu si', 'Ya basta de bromas, aqui esta el si', 'Okey, Ahora creo que esta más claro presiona aqui para el si', 'Ya presiona el si', 'Claro que si todo lo que tu digas <3']
const numberReject =ref(0)
function showQuestion(){
    backAudio.value.play()
    backAudio.value.volume = 0.1
    isOpenQuestion.value = true
}
function isNot(){
    sizeReject.value+=20
    heightReject.value+=4
    numberReject.value++
}
function isYes(){
    isNotResponse.value = false
}
</script>
<template>
    <div
    class="flex justify-center bg-full w-full h-full items-center p-2 overflow-hidden max-h-screen">
        <div v-if="!isOpenQuestion" class="overflow-hidden">
            <FGButton
            class="text-3xl p-5"
            text-button="Mostrar pregunta"
            @click="showQuestion">
            </FGButton>
        </div>
        <div v-else-if="isNotResponse"
        class="flex flex-col w-full h-full overflow-hidden">
            <div class="w-full text-center">
                <img src="@/assets/Question.png" class="w-xs h-xs">
            </div>  
            <p class="text-black text-center text-2xl font-bold">¿Quieres ser mi valentin?</p>
            <div class="flex flex-row gap-2 overflow-hidden">
                <FGButton 
                v-if="numberReject!=10"
                text-button="No" 
                class="bg-red border-white font-bold py-4 hover:border-0 hover:bg-red"
                @click="isNot"></FGButton>
                <FGButton 
                :text-button="textRespose[numberReject]" 
                class="bg-blue border-white font-bold py-4 hover:border-0"
                :style="[`width: ${sizeReject}%;`,`height: ${heightReject}rem;`]"
                @click="isYes"></FGButton>
            </div>
        </div>
        <div v-else
        class="flex flex-col w-full h-full overflow-hidden">
            <div class="w-full text-center">
                <img src="https://media.tenor.com/wWYDcbdOMWQAAAAM/cat-kiss-kiss-cat.gif" class="w-xs h-xs">
            </div>  
            <p class="text-black text-center text-2xl font-bold">Ya sabia que dirias que si, te quiero mucho</p>
            <p class="text-black text-center text-xl">Favor de comunicarse para acordar una bonita cita ♥</p>
        </div>        
    </div>
</template>