<template>
  <div>
    <div class="modelle" v-if="modelle">
      <Head>
        <Title>Schuhmodelle</Title>
        <Meta
          name="description"
          content="Schuhe nach Mass. Die Modelle in der Übersicht"
        />
      </Head>
      <div class="title">
        <h1>DIE MODELLE</h1>
      </div>
      <div class="line"></div>
      <div class="content">
        <div v-for="(modell, index) in modelle" :key="index">
          <div class="shoeheader">
            <h2 class="shoetitle">
              {{ modell.name }}
            </h2>
            <div class="price">ab CHF {{ modell.preis }}</div>
          </div>
          <SanityContent
            v-if="modell.beschreibung"
            :blocks="modell.beschreibung"
          />
          <div class="spacer" v-else></div>
          <div class="galerie">
            <img
              @click="resize"
              class="modellImage"
              v-for="(image, index) in modell.galerie.images"
              :key="index"
              :src="$urlFor(image.asset).auto('format').url()"
              :alt="modell.name"
              loading="lazy"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const resize = (e) => {
  var initHeight = 24.8;
  if (
    e.target.parentNode.style.height == "24.8vw" ||
    e.target.parentNode.style.height == ""
  ) {
    const myInterval = setInterval(() => {
      initHeight += 2;
      const images = [...e.target.parentNode.children];
      const imageIndex = images.indexOf(e.target);
      const vwInPx = document.documentElement.clientWidth / 100;
      console.log(initHeight);
      e.target.parentNode.style.height = initHeight + "vw";
      e.target.parentNode.scrollBy(2.5 * vwInPx * imageIndex, 0);

      if (initHeight > 51.9) {
        clearInterval(myInterval);
      }
    }, 10);
  } else {
    initHeight = 51.9;
    const myInterval = setInterval(() => {
      initHeight -= 2;
      const images = [...e.target.parentNode.children];
      const imageIndex = images.indexOf(e.target);

      const vwInPx = document.documentElement.clientWidth / 100;
      console.log(initHeight);
      e.target.parentNode.style.height = initHeight + "vw";
      e.target.parentNode.scrollBy(-2.5 * vwInPx * imageIndex, 0);

      if (initHeight < 25.7) {
        clearInterval(myInterval);
        e.target.parentNode.style.height = "24.8vw";
      }
    }, 10);
  }
};

const query = groq`*[_type == "modelle"] {name, beschreibung, galerie, preis}`;
const { data: modelle, refresh } = useSanityQuery(query);
</script>

<style>
.spacer {
  height: 2.5vw;
}
.galerie {
  margin-top: 1%;
  width: 100%;
  height: 24.8vw;
  display: inline-flex;
  gap: 3.5%;
  -ms-overflow-style: none; /* IE and Edge */
  scrollbar-width: none;
  overflow: scroll;
  cursor: pointer;
}
.galerie::-webkit-scrollbar {
  display: none;
}

.modellImage {
  height: 100%;
  aspect-ratio: 3 / 4;
  object-fit: cover;
}

.full {
  width: 40vw;
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

@media screen and (max-width: 900px) {
}
</style>
