<template>
  <div class="mk" @click="props.onClose">
    <div class="popup" @click.stop>
      <div class="header">Popup Header</div>
      <div class="content">Popup Content</div>
      <div class="footer">Popup Footer</div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { watchEffect } from 'vue';

const props = defineProps<{ onClose: () => void }>();
watchEffect((onInvalidate) => {
  const handleKeyPress = (event: KeyboardEvent) => {
    if (event.key === 'Escape') props.onClose();
  };

  window.addEventListener('keydown', handleKeyPress);

  onInvalidate(() => {
    window.removeEventListener('keydown', handleKeyPress);
  });
})

</script>

<style>
.mk {
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
  background-color: #00000060;

  .popup {
    border: .5px solid #e3e3e3;
    border-radius: 20px;
    width: 500px;
    height: 500px;
    background-color: #252525;
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: space-between;

    .header {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 4rem;
    }

    .content {
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .footer {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 4rem;
    }
  }
}
</style>