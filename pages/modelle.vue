<template>
  <div class="modelle">
    <div class="title">
      <h1>DIE MODELLE</h1>
    </div>
    <div class="line"></div>
    <div class="content" v-if="modelle">
      <div v-for="(modell, index) in modelle" :key="index">
        <div class="shoeheader">
          <h2 class="shoetitle">
            {{ modell.name }}
          </h2>
          <div class="price">CHF {{ modell.preis }}</div>
        </div>
        <SanityContent :blocks="modell.beschreibung" />
        <div class="galerie">
          <img
            v-for="(image, index) in modell.galerie.images"
            :key="index"
            class="modellImage"
            :src="$urlFor(image.asset).auto('format').width(500).url()"
            loading="lazy"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const full = false;

const query = groq`*[_type == "modelle"] {name, beschreibung, galerie, preis}`;
const { data: modelle } = useSanityQuery(query);
</script>

<style>
.galerie {
  display: inline-flex;
  margin-top: 1%;
  gap: 3.5%;
  -ms-overflow-style: none; /* IE and Edge */
  scrollbar-width: none;
  overflow: scroll;
}
.galerie::-webkit-scrollbar {
  display: none;
}

.modellImage {
  width: 25vw;
}

.full {
  height: 70vh !important;
  left: 50% !important;
  top: 0 !important;
  z-index: 10;
  transform: translateX(-50%);
  transition: all 0.5s;
}

.shoeheader {
  margin-top: 5%;
  display: flex;
}

.shoetitle {
  margin: 0;
  padding-right: 3rem;
  padding-left: 0.6rem;
  transform: translateX(-0.6rem);
}

.price {
  font-size: 1.3rem;
  align-self: flex-end;
  margin-left: 0.5rem;
  transform: translateY(0.45rem);
}
</style>
