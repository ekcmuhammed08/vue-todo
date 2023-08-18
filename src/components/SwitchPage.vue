<script setup>


const props = defineProps({
  currentPage:String,
  handlePage:{type:Function,
    },
});


</script>

<template>
      <div class="w-[350px] sm:w-[410px] mb-16">
          <button :class="`border border-r-white border-transparent ${currentPage === 'Active' ? 'bg-[#41B883] drop-shadow-[0_2px_2px_rgba(65,184,131,1)]' : 'bg-gray-300'}  p-4 w-1/3 text-center font-medium hover:bg-[#41b88380] `" @click="handlePage('Active')">Active</button>
          <button :class="`border border-x-white border-transparent ${currentPage === 'Completed' ? 'bg-[#41B883] drop-shadow-[0_2px_2px_rgba(65,184,131,1)]' : 'bg-gray-300'}  p-4 w-1/3 text-center font-medium hover:bg-[#41b88380] `" @click="handlePage('Completed')">Completed</button>
          <button :class="`border border-l-white border-transparent ${currentPage === 'All' ? 'bg-[#41B883] drop-shadow-[0_2px_2px_rgba(65,184,131,1)]' : 'bg-gray-300'}  p-4 w-1/3 text-center font-medium hover:bg-[#41b88380] `" @click="handlePage('All')">All</button>
      </div>
</template>