<template>
  <!-- <p>Worked with {{ selectedImage }}</p> -->
</template>
<script setup>
import { ref, onMounted } from "vue";

const props = defineProps({
  // where to find avatar's parts
  options: {
    type: Array,
    required: true,
  },
  // canvas info
  canvasWidth: {
    type: Number,
    required: true,
  },
  canvasHeight: {
    type: Number,
    required: true,
  },
  canvasRef: {
    required: true,
  },
  // part info
  // offset from lrft
  left: {
    type: Number,
    default: 0,
  },
  // offset from top
  top: {
    type: Number,
    default: 0,
  },
  // rotate part
  rotate: {
    type: Number,
    default: null,
  },
  // some exceptions
  exceptions: {
    type: Array,
    default: [],
  },
});

const selectedImage = ref("");

const draw = () => {
  const image = new Image();
  image.src = selectedImage.value;

  image.onload = () => {
    // declare for drawings
    const ctx = props.canvasRef.getContext("2d");
    // const scaleFactor = Math.min(1, Math.min(props.canvasWidth / image.width, props.canvasHeight / image.height))
    // passed by user left position doesnt take into account the image's width, fix this
    var new_left = props.left;
    if (new_left !== 0) new_left -= image.width / 2;
    var new_top = props.top;
    if (props.exceptions.includes(selectedImage.value))
      new_top -= (image.height / 2) * 0.75;

    if (props.rotate !== null) {
      ctx.translate(new_left + image.width / 2, new_top + image.height / 2);
      ctx.rotate((Math.PI / 180) * props.rotate); // Convert degrees to radians for rotation
      new_left = -image.width / 2;
      new_top = -image.height / 2;
    }
    // draw
    ctx.drawImage(image, new_left, new_top, image.width, image.height);
  };
};

onMounted(() => {
  // get random image
  selectedImage.value =
    props.options[Math.floor(Math.random() * props.options.length)];
  // console.log(selectedImage.value);

  draw();
});
</script>
