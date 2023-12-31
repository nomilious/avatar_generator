<script setup props="props">
import { ref, onMounted } from 'vue';

const props = defineProps({
    options: {
        type: Array,
        required: true 
    },
    canvasWidth: {
        type: Number,
        required: true
    },
    canvasHeight: {
        type: Number,
        required: true
    },
    canvasRef: {
        type: Object,
        required: true
    },
    left: {
        type: Number,
        default: 0
    },
    top: {
        type: Number,
        default: 0 
    }
});

const selectedImage = ref('');

const draw = () => { 
    const image = new Image();
    image.src = selectedImage.value;

    image.onload = () => { 
        // declare for drawings
        const ctx = props.canvasRef.getContext('2d');
        // scale givven image to 400*400
        // const scaleFactor = Math.min(1, Math.min(props.canvasWidth / image.width, props.canvasHeight / image.height))
        // passed by user left position doesnt take into account the image's width, fix this
        const scaleFactor = 1
        var new_left = props.left
        if (new_left !== 0)
            new_left -= image.width / 2
        var new_top = props.top
        // if (new_top !== 0)
        //     new_top += image.height / 2
        // draw
        ctx.drawImage(image, new_left, new_top,
            image.width* scaleFactor,
            image.height* scaleFactor
        );
    }
}

onMounted(() => {
    // get random image
    selectedImage.value = props.options[
        Math.floor(Math.random() * props.options.length)
    ];
    console.log(selectedImage)
    draw()
});
</script>
