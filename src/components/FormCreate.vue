<template>
  <h2>Форма создания</h2>
  <form @submit.prevent="addCard" class="form">
    <label for="title">
      <span>Название:</span>
      <input id="title" type="text" v-model="newCard.title" />
    </label>
    <label for="description">
      <span>Описание:</span>
      <input type="text" id="description" v-model="newCard.description" />
    </label>
    <button type="submit">Добавить</button>
  </form>
</template>

<script setup>
import { ref } from "vue";

const emit = defineEmits(["set-card"]);
const newCard = ref({
  id: 0,
  title: "",
  description: "",
  completed: false,
});

const addCard = () => {
  emit("set-card", newCard.value);
  console.log(newCard.value);
};
</script>

<style scoped>
.form {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  margin-bottom: 12px;
}

input {
  margin-left: 4px;
  margin-bottom: 8px;
}
</style>
