<!-- <template>
  <div>
    <canvas ref="canvas" width="440" height="440">
      <Componen :options="headOptions" />
      <Componen :options="backgroundOptions" />
    </canvas>
    
    <button @click="downloadAvatar">Download Avatar</button>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import Componen from './components/Componen.vue';

const canvasRef = ref(null);

const headOptions = [
  "./img/head/Head.png"
];
const backgroundOptions = [
  "./img/background/Boom.png",
  "./img/background/Bricks.png",
  "./img/background/Solid copy.png",
  "./img/background/Solid-2.png",
  "./img/background/Solid.png",
];
// ... Define other options for different components

const downloadAvatar = () => {
  const canvas = canvasRef.value;
  const ctx = canvas.getContext('2d');

  // Clear canvas before drawing
  ctx.clearRect(0, 0, canvas.width, canvas.height);

  // Draw each component onto the canvas
  drawComponents(ctx, [headOptions, backgroundOptions]);
  // ... Draw other components in a similar way

  // Generate a PNG image from the canvas and trigger download
  const downloadLink = document.createElement('a');
  downloadLink.href = canvas.toDataURL('image/png');
  downloadLink.download = 'avatar.png';
  downloadLink.click();
};

const drawComponents = (ctx, components) => {
  let offsetY = 0; // Offset to position components vertically

  components.forEach(options => {
    const img = new Image();
    img.src = options[Math.floor(Math.random() * options.length)];
    img.onload = () => {
      ctx.drawImage(img, 0, offsetY, canvasRef.value.width, canvasRef.value.height);
      offsetY += canvasRef.value.height; // Increase Y position for the next component
    };
  });
};
</script> -->

<template>
  <canvas ref="canvas" :width="canvasWidth" :height="canvasHeight"></canvas>
  <Component
    :options="backgroundOptions"
    :canvasWidth="canvasWidth"
    :canvasHeight="canvasHeight"
    :canvasRef="canvas"
  />
  <Component
    :options="headOptions"
    :canvasWidth="canvasWidth"
    :canvasHeight="canvasHeight"
    :canvasRef="canvas"
    :left="center"
    :top="headTop"
  />
  <Component
    :options="EyeOptions"
    :canvasWidth="canvasWidth"
    :canvasHeight="canvasHeight"
    :canvasRef="canvas"
    :left="center"
    :top="eyesTop"
  />

  <Component
    :options="bodyOptions"
    :canvasWidth="canvasWidth"
    :canvasHeight="canvasHeight"
    :canvasRef="canvas"
    :left="center"
    :top="bodyTop"
  />

  <Component
    :options="EyeBrowOptions"
    :canvasWidth="canvasWidth"
    :canvasHeight="canvasHeight"
    :canvasRef="canvas"
    :left="center"
    :top="eyebrowsTop"
  />
  <Component
    :options="GlassesOptions"
    :canvasWidth="canvasWidth"
    :canvasHeight="canvasHeight"
    :canvasRef="canvas"
    :left="center"
    :top="glassesTop"
  />
  <Component
    :options="hairOptions"
    :canvasWidth="canvasWidth"
    :canvasHeight="canvasHeight"
    :canvasRef="canvas"
    :left="center"
    :top="hairTop"
  />

  <Component
    :options="MouthOptions"
    :canvasWidth="canvasWidth"
    :canvasHeight="canvasHeight"
    :canvasRef="canvas"
    :left="center"
    :top="mouthTop"
  />
</template>

<script setup>
import { onMounted, ref } from "vue";
import Component from "./components/Component.vue";

const center = 220;
const headTop = 130;
const hairTop = 58;
const eyesTop = 200;
const eyebrowsTop = 178;
const bodyTop = 300;
const petTop = 100;
const mouthTop = 225;
const glassesTop = 194;

const headOptions = ["./img/head/Head.png"];
const backgroundOptions = [
  // "./img/background/Boom.png",
  // "./img/background/Bricks.png",
  // "./img/background/Solid copy.png",
  "./img/background/Solid-2.png",
  // "./img/background/Solid.png",
];
const bodyOptions = [
  // "./img/body/Muscle shirt.png",
  // "./img/body/Plain.png",
  "./img/body/Necklace.png",
  // "./img/body/Print.png",
  // "./img/body/Super hero.png",
  // "./img/body/Sweater.png",
];
const hairOptions = [
  // "./img/hair/Bun.png",
  // "./img/hair/Cap.png",
  // "./img/hair/Crazy.png",
  // "./img/hair/Curly.png",
  "./img/hair/Long.png",
  // "./img/hair/Mullet.png",
  // "./img/hair/Mohawk.png",
  // "./img/hair/Ninja.png",
  // "./img/hair/Ponytail.png",
  // "./img/hair/Smooth.png",
  // "./img/hair/Styled.png",
];
const MouthOptions = [
  // "./img/Mouth/Open Smile.png",
  // "./assets/Mouth/Beard 2.png",
  // "./assets/Mouth/Beard.png",
  // "./assets/Mouth/Line.png",
  "./img/Mouth/Lips.png",
  // "./assets/Mouth/Original.png",
  // "./assets/Mouth/Smile.png",
];
const EyeOptions = [
  "./img/Eye/Lashes.png",
  // "./img/Eye/Nice.png",
  // "./img/Eye/Normal.png",
  // "./img/Eye/Original.png",
  // "./img/Eye/Tired.png",
];
const GlassesOptions = [
  // "./img/glasses/Sunnies.png",
  "./img/glasses/Plain.png",
  // "./img/glasses/Reading.png",
];
const EyeBrowOptions = [
  // "./img/Eyebrows/Angry.png",
  // "./img/Eyebrows/Formed.png",
  "./img/Eyebrows/Round.png",
  // "./img/Eyebrows/Thick.png",
  // "./img/Eyebrows/Thin.png",
  // "./img/Eyebrows/Unsure.png",
];
// TODO write a script to get all names

const canvasWidth = ref(440);
const canvasHeight = ref(440);
const canvas = ref(null);
</script>
