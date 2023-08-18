<script setup>
import { ref } from 'vue';
import Pages from './components/Pages.vue'
import SwitchPage from './components/SwitchPage.vue';
import Input from './components/Input.vue';

const list = ref([]);
const newTask = ref('');
const currentPage = ref('All');

const addTask = () =>{
  list.value.push({task:newTask.value, isChecked: false})
  newTask.value = ''

}

const removeTask = (index) => {
  list.value.splice(index, 1);
  for(let i = 0; i<list.value.length; i++ ){
    document.getElementById(`checkbox-${i}`).checked  = list.value[i].isChecked
  }
};

const checkTask = (index) =>{
  list.value[index].isChecked = !list.value[index].isChecked
  for(let i = 0; i<list.value.length; i++ ){
    document.getElementById(`checkbox-${i}`).checked  = list.value[i].isChecked
  }
}

const handlePage = (page)=>{
  currentPage.value = page
}

</script>

<template>
  <header class="flex justify-center my-8">
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>
  <body>
    <div class="flex flex-col items-center">
    <Input :addTask="addTask"   
     :modelValue="newTask"
     @update:modelValue="newValue => newTask = newValue"/>
    <Pages :currentPage="currentPage" :list="list" :checkTask="checkTask" :removeTask="removeTask"/>
    <SwitchPage :currentPage="currentPage" :handlePage="handlePage"/>
    </div>
  </body>
</template>


