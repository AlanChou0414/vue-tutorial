<script setup lang="ts">
import { reactive } from 'vue';
import Popup from './components/Popup.vue';

const state = reactive({
  isOpen: false
});

const onClose = () => state.isOpen = false;
const onOpen = () => state.isOpen = true;

</script>

<template>
  <button class="btn" type="button" @click="onOpen">OPEN POPUP</button>
  <Popup v-if="state.isOpen" :onClose="onClose" />
</template>

<style>
.btn {
  background-color: #e3e3e3;
  color: #252525;
  border-radius: 10px;
  padding: 10px 20px;
}
</style>
