<template>
  <div className="container">
    <!-- <FormCreate @set-card="addCard" /> -->
    <FormEdit :card="cardForEdit" @set-card="updateCard" @save-card="saveCard" />
    <WishList :cards="cards" @click-by-card="openCardForEdit" />
  </div>
</template>

<script setup>
import { ref } from "vue";
import WishList from "./components/WishList.vue";
import FormCreate from "./components/FormCreate.vue";
import FormEdit from "./components/FormEdit.vue";
const cards = ref([
  {
    id: 1,
    title: "Ноутбук",
    description: "Я хочу получить в подарок новый ноутбук",
    completed: false,
  },
  {
    id: 2,
    title: "Наушники",
    description: "Я хочу получить в подарок наушники для ноутбука",
    completed: true,
  },
  {
    id: 3,
    title: "Мышка",
    description: "Я хочу получить в подарок мышку для ноутбука",
    completed: false,
  },
]);

const saveCard = () => {
  const newCard = Object.assign({}, cardForEdit.value);
  cards.value = cards.value.map((el) => (el.id === newCard.id ? newCard : el));
};

const cardForEdit = ref({
  id: 0,
  title: "",
  description: "",
  completed: false,
});

const openCardForEdit = (card) => {
  cardForEdit.value = Object.assign({}, card);
};

const updateCard = (card) => {
  cardForEdit.value = card;
};
</script>

<style scoped>
@import "./assets/global.css";
</style>
