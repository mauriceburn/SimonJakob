<template>
  <div class="container">
    <img
      v-if="linkData.background"
      class="background"
      :src="
        $urlFor(linkData.background).auto('format').width(700).height(700).url()
      "
      alt="Schuhmacherei Jakob"
    />
    <img
      v-if="linkData.overlay"
      class="overlay"
      :src="$urlFor(linkData.overlay).auto('format').width(700).url()"
      alt="Schuhmacherei Jakob"
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
  aspect-ratio: 1 / 1;
  object-fit: cover;
}

.container:hover .background {
  opacity: 1;
}
.container:active .background {
  opacity: 1;
}

.overlay {
  width: 70%;
  padding: 50% 15% 50% 15%;
  opacity: 1;
  transition: 0.3s ease;
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  margin: auto;
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
  letter-spacing: 0.2rem;
}

.overlay:hover {
  filter: invert(1);
}

.overlay:active {
  filter: invert(1);
}

.linkText:hover {
  color: white;
}

.linkText:active {
  color: white;
}

.right {
  width: 40%;
}

.right img {
  width: 100%;
}
</style>
