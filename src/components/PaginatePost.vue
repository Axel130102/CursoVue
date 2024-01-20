<script setup>

defineProps(["inicio", "fin", "MaxLength"])

const emit = defineEmits(['Next', 'Back'])

</script>

<template>
    <div class="p-5">
        <div class="flex justify-center items-baseline flex-wrap">
            <div class="flex m-2">
                <button class="text-base  rounded-r-none  hover:scale-110 focus:outline-none flex justify-center px-4 py-2 rounded font-bold cursor-pointer 
            hover:bg-sky-200  
            bg-sky-100 
            text-sky-700 
            border duration-200 ease-in-out 
            border-sky-600 transition
            disabled:cursor-not-allowed disabled:opacity-50 disabled:bg-gray-300 disabled:border-gray-300 disabled:text-gray-500"
            @click="emit('Back')"
            :disabled="inicio === 0"
            >
                    <div class="flex leading-5">
                        <svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-chevron-left w-5 h-5">
                            <polyline points="15 18 9 12 15 6"></polyline>
                        </svg>
                        Back</div>
                </button>
                <button class="text-base  rounded-l-none border-l-0  hover:scale-110 focus:outline-none flex justify-center px-4 py-2 rounded font-bold cursor-pointer 
            hover:bg-blue-200  
            bg-blue-100 
            text-blue-700 
            border duration-200 ease-in-out 
            border-blue-600 transition
            disabled:cursor-not-allowed disabled:opacity-50 disabled:bg-gray-300 disabled:border-gray-300 disabled:text-gray-500"
            @click="emit('Next')"
            :disabled="fin >= MaxLength"
            >
                    <div class="flex leading-5">Next
                        <svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-chevron-right w-5 h-5 ml-1">
                            <polyline points="9 18 15 12 9 6"></polyline>
                        </svg>
                    </div>
                </button>
            </div>
        
        </div>

    </div>
</template>