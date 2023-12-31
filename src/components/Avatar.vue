<template class="container">
  <div :key="componentKey">
    <main class="app-main">
      <canvas ref="canvas" :width="canvasWidth" :height="canvasHeight"></canvas>
      <div class="buttons-container">
        <button @click="downloadAvatar" class="download-button">
          <i class="fas fa-download"></i> Скачать
        </button>
        <button @click="regenerateAvatar" class="regenerate-button">
          <i class="fas fa-redo"></i> Перегенерировать
        </button>
      </div>
    </main>
    <!-- mainpart   rendering is inside of AvatarPart-->
    <template v-for="part in avatarParts">
      <AvatarPart
        :options="part.options"
        :canvasWidth="canvasWidth"
        :canvasHeight="canvasHeight"
        :canvasRef="canvas"
        :left="part.left || 0"
        :top="part.top || 0"
        :rotate="part.rotate || null"
        :exceptions="part.exceptions || []"
      />
    </template>
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue";
import {
  headOptions,
  backgroundOptions,
  petOptions,
  bodyOptions,
  hairOptions,
  MouthOptions,
  MouthExcepions,
  EyeOptions,
  GlassesOptions,
  EyeBrowOptions,
} from "../avatarPartsPath";
import AvatarPart from "./AvatarPart.vue";

const canvasWidth = ref(440);
const canvasHeight = ref(440);
const canvas = ref(null);
const ppp = ref(null);
const componentKey = ref(0);

const center = canvasWidth.value / 2;
const headTop = 125.01;
const hairTop = 58;
const eyesTop = 200;
const eyebrowsTop = 176.67;
const bodyTop = 297.21;
const mouthTop = 225;
const glassesTop = 192;
const petTop = 300;
const petLeft = 90;

const avatarParts = [
  {
    options: backgroundOptions,
  },
  {
    options: headOptions,
    left: center,
    top: headTop,
  },
  {
    options: EyeOptions,
    left: center,
    top: eyesTop,
  },
  {
    options: bodyOptions,
    left: center,
    top: bodyTop,
  },
  {
    options: EyeBrowOptions,
    left: center,
    top: eyebrowsTop,
  },
  {
    options: GlassesOptions,
    left: center,
    top: glassesTop,
  },
  {
    options: MouthOptions,
    left: center,
    top: mouthTop,
    exceptions: MouthExcepions,
  },
  {
    options: hairOptions,
    left: center,
    top: hairTop,
  },
  {
    options: petOptions,
    left: petLeft,
    top: petTop,
    rotate: -20,
  },
];

const regenerateAvatar = () => {
  componentKey.value++;
  console.clear();
};

const downloadAvatar = () => {
  const dataURL = canvas.value.toDataURL("image/png");

  // Create a link element
  const link = document.createElement("a");
  link.href = dataURL;
  link.download = "avatar.png"; // Set the download file name

  // Trigger the click event on the link to start the download
  link.click();
};

// TODO write a script to get all names
</script>
<style>
/* Style for the canvas */
canvas {
  border: 1px solid #ccc;
  margin-top: 20px;
}
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.download-button {
  background-color: #3498db; /* Blue color for download button */
}

.regenerate-button {
  background-color: #27ae60; /* Green color for regenerate button */
}

.app-main {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
}

canvas {
  margin-bottom: 20px;
  border: no;
}

.buttons-container {
  white-space: nowrap;
  display: flex;
  justify-content: center;
  gap: 1%;
}
.buttons-container botton {
  transition: opacity 0.3s ease;
}
.buttons-container button:hover {
  opacity: 0.8; /* Reduce opacity on hover (adjust as needed) */
}

.buttons-container button:hover i {
  transition: transform 0.3s ease; /* Transition for icon scaling */
  transform: scale(1.2); /* Scale up the icon on hover (adjust as needed) */
}
button {
  margin: 8px;
  padding: 10px 15px;
  background-color: #3498db;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
</style>
