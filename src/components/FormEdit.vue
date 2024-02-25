<template>
  <h2>Форма редактирования</h2>
  <form @submit.prevent="saveCard" class="form">
    <label for="title">
      <span>Название:</span>
      <input id="title" type="text" :value="card.title" @input="setTitle" />
    </label>
    <label for="description">
      <span>Описание:</span>
      <input type="text" id="description" :value="card.description" @input="setDescription" />
    </label>
    <button type="submit">Сохранить</button>
  </form>
</template>

<script setup>
const emit = defineEmits(["set-card", "save-card"]);
const props = defineProps({
  card: {
    type: Object,
  },
});

const setTitle = (e) => {
  const data = Object.assign({}, props.card);
  data.title = e.target.value;
  emit("set-card", data);
};

const setDescription = (e) => {
  const data = Object.assign({}, props.card);
  data.description = e.target.value;
  emit("set-card", data);
};

const saveCard = () => {
  emit("save-card");
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
