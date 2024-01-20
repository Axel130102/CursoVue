<script setup>

defineProps({
    id: Number,
    title: String,
    body: {
        type: String,
        default: 'Contenido ejemplo'
    },
})

const emit = defineEmits(['cambiarFavoritoNombre'])

</script>


<template>
<div class="shadow-2xl p-3 m-3 rounded-xl w-auto bg-slate-300 flex flex-col">
    <h1 class="border-b-2 border-black text-2xl text-center h-24">{{ id }} - {{ title }}</h1>
    <p class="text-[#000] my-5 h-40">{{ body }}</p>
    <button 
    class="hover:scale-110 focus:outline-none px-4 py-2 rounded self-end cursor-pointer hover:bg-blue-200 bg-blue-100 text-blue-700 border duration-200 ease-in-out border-blue-600 transition"
    @click="emit('cambiarFavoritoNombre',this.id, this.title)"
    >
    <div class="flex leading-5">
        Favorito
    </div>
    </button>



</div>

    
</template>