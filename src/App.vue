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
    :options="MouthOptions"
    :canvasWidth="canvasWidth"
    :canvasHeight="canvasHeight"
    :canvasRef="canvas"
    :left="center"
    :top="mouthTop"
    :exceptions="MouthExcepions"
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
    :options="petOptions"
    :canvasWidth="canvasWidth"
    :canvasHeight="canvasHeight"
    :canvasRef="canvas"
    :left="petLeft"
    :top="petTop"
    :rotate="-20"
  />
</template>

<script setup>
import { onMounted, ref } from "vue";
import Component from "./components/Component.vue";

const center = 220;
const headTop = 125.01;
const hairTop = 57.54;
const eyesTop = 199.94;
const eyebrowsTop = 176.67;
const bodyTop = 297.21;
const mouthTop = 225;
const glassesTop = 192;
const petTop = 300;
const petLeft = 90;

const headOptions = ["./img/head/Head.png"];
const backgroundOptions = [
  "./img/background/Boom.png",
  "./img/background/Bricks.png",
  "./img/background/Solid copy.png",
  "./img/background/Solid-2.png",
  "./img/background/Solid.png",
];
const petOptions = [
  "./img/pet/Cat.png",
  "./img/pet/Dog.png",
  "./img/pet/Fish.png",
  "./img/pet/Raptor.png",
];
const bodyOptions = [
  "./img/body/Muscle shirt.png",
  "./img/body/Plain.png",
  "./img/body/Necklace.png",
  "./img/body/Print.png",
  "./img/body/Super hero.png",
  "./img/body/Sweater.png",
];
const hairOptions = [
  "./img/hair/Bun.png",
  "./img/hair/Cap.png",
  "./img/hair/Crazy.png",
  "./img/hair/Curly.png",
  "./img/hair/Long.png",
  "./img/hair/Mullet.png",
  "./img/hair/Mohawk.png",
  "./img/hair/Ninja.png",
  "./img/hair/Ponytail.png",
  "./img/hair/Smooth.png",
  "./img/hair/Styled.png",
];
const MouthOptions = [
  "./img/Mouth/Open Smile.png",
  "./img/Mouth/Beard 2.png",
  "./img/Mouth/Beard.png",
  "./img/Mouth/Line.png",
  "./img/Mouth/Lips.png",
  "./img/Mouth/Original.png",
  "./img/Mouth/Smile.png",
];
const MouthExcepions = ["./img/Mouth/Beard 2.png"];
const EyeOptions = [
  "./img/Eye/Lashes.png",
  "./img/Eye/Nice.png",
  "./img/Eye/Normal.png",
  "./img/Eye/Original.png",
  "./img/Eye/Tired.png",
];
const GlassesOptions = [
  "./img/glasses/Sunnies.png",
  "./img/glasses/Plain.png",
  "./img/glasses/Reading.png",
];
const EyeBrowOptions = [
  "./img/Eyebrows/Angry.png",
  "./img/Eyebrows/Formed.png",
  "./img/Eyebrows/Round.png",
  "./img/Eyebrows/Thick.png",
  "./img/Eyebrows/Thin.png",
  "./img/Eyebrows/Unsure.png",
];
// TODO write a script to get all names

const canvasWidth = ref(440);
const canvasHeight = ref(440);
const canvas = ref(null);
</script>
