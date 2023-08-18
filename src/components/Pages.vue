<script setup>
import CloseBox from 'vue-material-design-icons/CloseBox.vue';
import checkboxIntermediate from 'vue-material-design-icons/checkboxIntermediate.vue';
import checkboxBlankOutline from 'vue-material-design-icons/checkboxBlankOutline.vue';


const props = defineProps({
  currentPage:String,
  list:Array,
  checkTask:{type:Function,
    },
  removeTask:{type:Function,
    },
});


</script>

<template>
    <div class="flex w-96 justify-between">
    </div>
     <div :class="`border bg-[#FAFAFA] py-6 px-4 m-4 rounded ${currentPage!='All' && 'hidden'}`">
        <div class="flex flex-col w-96">
          <div v-for="(task, index) in list" :key="index" class="flex flex-row justify-between p-2 m-2 border bg-[#F0F0F0] hover:bg-gradient-to-r from-[#FaFaFa] from-40% to-[#41b8831a] to-90% rounded drop-shadow-[0_2px_2px_rgba(65,184,131,1)]" style="overflow-wrap: anywhere;">            
            <div class="flex">
                <label :for="`checkbox-${index}`">
                    <checkbox-blank-outline style="color: #34495E;" size="32px" :class="`${task.isChecked&&'hidden'}`"/>
                    <checkbox-intermediate style="color: #34495E;" size="32px" :class="`${!task.isChecked&&'hidden'}`"/> 
                    <input class="w-6 hidden" style="accent-color: #34495E;" type="checkbox" :id="`checkbox-${index}`" @click="checkTask(index)">
                </label>
              <p :class="`pl-3 pb-1 ${task.isChecked?'line-through':''}`">{{ task.task }}</p>
            </div>
            <button @click="removeTask(index)" class=" h-full w-full drop-shadow-[0_0_3px_rgba(65,184,131,1)] hover:drop-shadow-[0_0_6px_rgba(65,184,131,1)]"><close-box style="color: #34495E;" size="24px" /> </button>
          </div>
        </div>
    </div>

      <div :class="`border bg-[#FAFAFA] py-6 px-4 m-4 rounded ${currentPage!='Completed' && 'hidden'}`">
        <div class="flex flex-col w-96">
          <div v-for="(task, index) in list" :key="index" >
            <div v-if="task.isChecked" class="flex flex-row justify-between p-2 m-2 border bg-[#F0F0F0] hover:bg-gradient-to-r from-[#FaFaFa] from-40% to-[#41b8831a] to-90% rounded drop-shadow-[0_2px_2px_rgba(65,184,131,1)]">
              <div class="flex">
                <label :for="`checkbox-${index}`">
                    <checkbox-blank-outline style="color: #34495E;" size="32px" :class="`${task.isChecked&&'hidden'}`"/>
                    <checkbox-intermediate style="color: #34495E;" size="32px" :class="`${!task.isChecked&&'hidden'}`"/> 
                    <input class="w-6 hidden" style="accent-color: #34495E;" type="checkbox" :id="`checkbox-${index}`" @click="checkTask(index)">
                </label>
                <p :class="`pl-3 pb-1 ${task.isChecked?'line-through':''}`">{{ task.task }}</p>
              </div>
              <button @click="removeTask(index)"><close-box style="color: #34495E;" size="24px"/> </button>
            </div>
          </div>
        </div>
      </div>

      <div :class="`border bg-[#FAFAFA] py-6 px-4 m-4 rounded ${currentPage!='Active' && 'hidden'}`">
        <div class="flex flex-col w-96">
          <div v-for="(task, index) in list" :key="index">
            <div v-if="!task.isChecked" class="flex flex-row justify-between p-2 m-2 border bg-[#F0F0F0] hover:bg-gradient-to-r from-[#FaFaFa] from-40% to-[#41b8831a] to-90% rounded drop-shadow-[0_2px_2px_rgba(65,184,131,1)]">
              <div class="flex">
                <label :for="`checkbox-${index}`">
                    <checkbox-blank-outline style="color: #34495E;" size="32px" :class="`${task.isChecked&&'hidden'}`"/>
                    <checkbox-intermediate style="color: #34495E;" size="32px" :class="`${!task.isChecked&&'hidden'}`"/> 
                    <input class="w-6 hidden" style="accent-color: #34495E;" type="checkbox" :id="`checkbox-${index}`" @click="checkTask(index)">
                </label>
                <p :class="`pl-3 pb-1 ${task.isChecked?'line-through':''}`">{{ task.task }}</p>
              </div>
              <button @click="removeTask(index)"><close-box style="color: #34495E;" size="24px"/> </button>
            </div>
          </div>
        </div>
      </div>
</template>