<script setup>
import {ref, reactive} from 'vue'
const images = [
    {
        id: 1,
        img:'/images/pic1.jpg'
    },
    {
        id: 2,
        img:'/images/pic2.jpg'
    },
    {
        id: 3,
        img:'/images/pic3.jpg'
    },
    {
        id: 4,
        img:'/images/pic4.jpg'
    }
]
const activeIndex = ref(0)
const activeImage = ref(images[0].img)
setInterval(indexNumber, 10000);
function indexNumber(value='right') {
    if ('left' == value) {
        if (0>=activeIndex.value) {
            activeIndex.value = images.length-1
        } else {
            activeIndex.value = activeIndex.value-1
        }
    } else if (images.length-1 <= activeIndex.value) {
        activeIndex.value = 0
    } else {
        activeIndex.value = activeIndex.value+1
    }
    activeImage.value = images[activeIndex.value].img
}

</script>
<template>
    <div class="image_carousel">
        <div class="nav_button">
            <div class="button_nav button_left">
                <button @click="indexNumber('left')" class="carousel_btn left"><font-awesome-icon :icon="['fas', 'angle-left']" /></button>
            </div>
            <div class="button_nav button_right">
                <button @click="indexNumber" class="carousel_btn right"><font-awesome-icon :icon="['fas', 'angle-right']" /></button>
            </div>
        </div>
        <div class="carousel_images">
            <div class="image_item">
                <img :src="activeImage">
            </div>
        </div>
    </div>
</template>
<style scoped>
.image_item img {
    margin: auto;
    display: block;
    width: 100%;
    height: 550px;
}
.nav_button .button_nav{
    position: absolute;
    z-index: 1;
    top: -50px;
    bottom: 0;
    transform: translateY(50%);
}
.nav_button button {
    width: 50px;
    height: 50px;
    border: 0;
    border-radius: 50%;
    cursor: pointer;
}
.image_carousel {
    position: relative;
    position: relative;
    margin: auto;
    width: 80%;
}
.button_nav.button_left {
    left: 50px;
}
.button_nav.button_right {
    right: 50px;
}
</style>