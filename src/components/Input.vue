<script setup>
import PlusBox from 'vue-material-design-icons/PlusBox.vue';

const props = defineProps({
  newTask:String,
  modelValue:String,
  addTask:{type:Function,
    },
});
defineEmits(['update:modelValue'])


</script>

<template>
      <div class="flex w-80 sm:w-96">
        <input 
        class="h-12 w-80 sm:w-96 pl-4 pr-10 rounded border-2 border-transparent focus:border-green-300 outline-none drop-shadow-[0_2px_2px_rgba(65,184,131,1)]"
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.value)"
        @keyup.enter="addTask"
        placeholder="Enter a new item" />
        
        <button @click="addTask" 
        class="bg-white mt-2.5 h-6 -ml-10 z-10"
        >
        <plus-box style="color: #34495E;" size="28px" class=" h-full w-full drop-shadow-[0_0_3px_rgba(65,184,131,1)] hover:drop-shadow-[0_0_6px_rgba(65,184,131,1)]"/>
        </button>
      </div>
</template>