<template>
  <h1>Wish list</h1>

  <AppCard
    v-for="(card, index) in cards"
    :key="card.id"
    :card="card"
    :index="index"
    @click="($event) => emit('click-by-card', card)" />
</template>

<script setup>
import AppCard from "./AppCard.vue";
const props = defineProps({
  cards: {
    type: Array,
    default: () => [],
  },
});

const emit = defineEmits(["click-by-card"]);
</script>

<style scoped></style>
