<template>
  <img
    class="inlineImage"
    :src="$urlFor(asset._ref).auto('format').width(700).url()"
    alt="Bild Schuhmacherei Jakob Bern"
    loading="lazy"
  />
</template>

<script setup>
const props = defineProps({
  asset: {},
});
</script>

<style>
.inlineImage {
  width: 46.5%;
  display: inline;
  margin: 1.7% 1.7% 1.7% 1.7%;
  aspect-ratio: 1 / 1;
}

@media screen and (max-width: 900px) {
  .inlineImage {
    width: 100%;
  }
}
</style>
