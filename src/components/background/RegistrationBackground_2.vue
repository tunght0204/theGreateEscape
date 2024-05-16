<template>
  <div class="registration-background-2">
    <div class="left">
      <div v-motion-slide-visible-left class="image-wrapper">
        <img
          src="@/assets/main/s5i1.png"
          @mouseover="setMonkey('monkey1', true)"
          @mouseout="setMonkey('monkey1', false)"
          style="top: 0"
        />
        <img
          src="@/assets/main/s5i2.png"
          @mouseover="setMonkey('monkey2', true)"
          @mouseout="setMonkey('monkey2', false)"
          style="top: 100px"
        />
        <img
          src="@/assets/main/s5i3.png"
          @mouseover="setMonkey('monkey3', true)"
          @mouseout="setMonkey('monkey3', false)"
          style="top: 200px"
        />
        <img
          src="@/assets/main/s5i4.png"
          @mouseover="setMonkey('monkey4', true)"
          @mouseout="setMonkey('monkey4', false)"
          style="top: 300px"
        />
        <img
          src="@/assets/main/s5i6.png"
          @mouseover="setMonkey('monkey5', true)"
          @mouseout="setMonkey('monkey5', false)"
          style="top: 400px"
        />
        <img
          src="@/assets/main/s5i52.png"
          @mouseover="setMonkey('monkey6', true)"
          @mouseout="setMonkey('monkey6', false)"
          style="top: 600px"
        />
      </div>
    </div>
    <div class="middle"></div>
    <div class="right">
      <div class="image-wrapper-2">
        <img v-show="monkeyList.monkey1" src="@/assets/main/slide4img1.png" />
        <img v-show="monkeyList.monkey2" src="@/assets/main/bgChimp.png" />
        <img v-show="monkeyList.monkey3" src="@/assets/main/bgGorilla.png" />
        <img v-show="monkeyList.monkey4" src="@/assets/main/bgGibbon.png" />
        <img v-show="monkeyList.monkey5" src="@/assets/main/perso-Chimpanzee.png" />
        <img v-show="monkeyList.monkey6" src="@/assets/main/bgBonobo.png" />
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { ref } from 'vue'

interface MonkeyList {
  monkey1: boolean
  monkey2: boolean
  monkey3: boolean
  monkey4: boolean
  monkey5: boolean
  monkey6: boolean
}

const monkeyList = ref<MonkeyList>({
  monkey1: true,
  monkey2: false,
  monkey3: false,
  monkey4: false,
  monkey5: false,
  monkey6: false
})

const setMonkey = (monkey: keyof MonkeyList, value: boolean) => {
  if (monkeyList.value.monkey1) {
    monkeyList.value.monkey1 = false
  }
  monkeyList.value[monkey] = value
}
</script>
<style scoped>
.registration-background-2 {
  height: 100vh;
  background-image: url('@/assets/main/bgmap2.jpg');
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
  top: 300px;
  left: 50px;
  width: 100%;
  height: 100%;

  img {
    height: 200px;
  }

  img:hover {
    transform: scale(1.5);
  }
}

.image-wrapper-2 {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.image-wrapper-2 img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
</style>
