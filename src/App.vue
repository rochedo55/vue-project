<script setup lang="ts">
import Tabs from "./components/Tabs.vue";
</script>

<template>
  <Tabs
    :tabButtons="['Aba 1', 'Aba 2', 'Aba 3']"
    :content="['conteudo da aba 1', 'conteudo da aba 2', 'conteudo da aba 3']"
  ></Tabs>
</template>

<style>
@import "./assets/base.css";
</style>
