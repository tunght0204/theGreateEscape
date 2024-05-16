<template>
  <div class="registration-container">
    <div class="form-container">
      <div><RegistrationForm /></div>
    </div>
    <div class="background-container">
      <RegistrationBackground_1 v-motion-slide-visible-left />
      <RegistrationBackground_2 v-motion-slide-visible-bottom />
      <RegistrationBackground_3 v-motion-slide-visible-left />
    </div>
  </div>
</template>

<script setup lang="ts">
import RegistrationBackground_1 from '../background/RegistrationBackground_1.vue'
import RegistrationBackground_2 from '../background/RegistrationBackground_2.vue'
import RegistrationBackground_3 from '../background/RegistrationBackground_3.vue'
import RegistrationForm from './RegistrationForm.vue'
</script>

<style scoped>
.registration-container {
  position: relative;
  height: 100vh;
}

.form-container {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -35%);
  z-index: 1;
}

.background-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow-y: auto;
}

.before-enter {
  opacity: 0;
  transform: translateY(100px);
  transition: all 2s ease-out;
}

.enter {
  opacity: 1;
  transform: translateY(0px);
}
</style>
