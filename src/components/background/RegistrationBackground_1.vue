<template>
  <div class="registration-background-1">
    <div class="left">
      <div class="image-wrapper">
        <img src="@/assets/main/perso-Chimpanzee.png" class="jump-monkey" />
        <img src="@/assets/main/land.png" />
      </div>
    </div>
    <div class="middle"></div>
    <div class="right">
      <div class="image-wrapper">
        <img src="@/assets/main/logotge.png" class="jump-monkey" />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped>
.registration-background-1 {
  height: 100vh;
  background-image: url('@/assets/main/mainBG.jpg');
  display: flex;
}

.left,
.right {
  position: relative;
  flex: 1;
}

.middle {
  width: 500px;
}

.image-wrapper {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.image-wrapper img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.jump-monkey {
  animation: jump 1s ease infinite;
  height: 80%;
}
</style>
