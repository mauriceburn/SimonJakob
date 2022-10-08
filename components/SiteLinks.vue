<template>
  <div class="container">
    <img v-if="linkData.background" class="background"
      :src="$urlFor(linkData.background).auto('format').width(700).height(700).url()"
      loading="lazy"
    />
    <img v-if="linkData.overlay" class="overlay"
      :src="$urlFor(linkData.overlay).auto('format').width(700).url()"
      loading="lazy"
    />
    <div v-if="linkData.linkText" class="linkText">{{ linkData.linkText }}</div>
  </div>
</template>

<script setup>
const props = defineProps({
  linkData: "",
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
  padding: 11% 15%;
  opacity: 1;
  transition: 0.3s ease;
  position: absolute;
  left: 0;
  top: 0;
}

.linkText {
  width: 100%;
  opacity: 1;
  transition: 0.3s ease;
  position: absolute;
  left: 0;
  top: 0;
  padding: calc(50% - 1.5rem) 0;
  text-align: center;
  font-size: 2rem;
}

.overlay:hover {
  filter: invert(1);
}

.linkText:hover {
  color: white;
}


.right {
  width: 40%;
}

.right img {
  width: 100%;
}
</style>
