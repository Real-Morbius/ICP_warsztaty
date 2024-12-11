<script setup>
import { ref } from 'vue';
import { my_project_backend } from 'declarations/my_project_backend/index';
let greeting = ref('');

async function handleSubmit(e) {
  e.preventDefault();
  const target = e.target;
  const name = target.querySelector('#name').value;
  await my_project_backend.greet(name).then((response) => {
    greeting.value = response;
  });
}
</script>

<template>
  <header>
    <img src="/logo2.svg" alt="DFINITY logo" />
    <br />
    <br />
    <form  class="flex flex-col gap-4 justify-center items-center bg-gray-9" action="#" @submit="handleSubmit">
      <label  class="text-2xl" for="name">Enter your name: &nbsp;</label>
      <input class="border-2 border-violet-600 width-50 text-black" id="name" alt="Name" type="text" />
      <button type="submit" class="bg-gradient-to-r from-violet-800 to-violet-950 text-violet-50 rounded-lg">Click Me!</button>
    </form>
    <section id="greeting">{{ greeting }}</section>
  </header>
</template>

<script>
export default  {
    name: "Header",
};
</script>
