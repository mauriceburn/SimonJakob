<template>
  <div class="container">
    <SanityImage class="background" :asset-id="bgImage" w="700" auto="format" />
    <SanityImage class="overlay" :asset-id="ovImage" w="700" auto="format" />
  </div>
</template>

<script setup>
const props = defineProps({
  bgImage: "",
  ovImage: "",
});
</script>

<style>
.container {
  opacity: 1;
  position: relative;
}

.background {
  width: 100%;
  opacity: 0.75;
  transition: 0.3s ease;
}

.container:hover .background {
  opacity: 1;
}

.overlay {
  width: 70%;
  padding: 10% 15% 8% 15%;
  opacity: 1;
  /* transform: translateY(-101%); */
  transition: 0.3s ease;
  position: absolute;
  left: 0;
  top: 0;
}

.overlay:hover {
  filter: invert(1);
}
</style>
