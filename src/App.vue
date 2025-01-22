<script setup>
import { ref } from 'vue';
import LicencePlate from "./components/LicencePlate.vue";
import { toPng, toJpeg, toBlob, toPixelData, toSvg } from 'html-to-image';

const plate = ref(null);

const render = () => {
  var node = plate.value.$el;

  toPng(node)
    .then(function (dataUrl) {
      var img = new Image();
      img.src = dataUrl;
      document.body.appendChild(img);
    })
    .catch(function (error) {
      console.error('oops, something went wrong!', error);
    });
};
</script>

<template>
  <div>
    <LicencePlate ref="plate" />
    <button @click="render">Render that up bro</button>
  </div>
</template>

<style>
@import url("/src/assets/fonts.css");
</style>
