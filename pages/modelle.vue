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
              <div class="price">CHF {{ modell.preis }}</div>
            </div>
            <SanityContent :blocks="modell.beschreibung" />
            <div class="galerie">
              <img
                @click="resize"
                class="modellImage"
                v-for="(image, index) in modell.galerie.images"
                :key="index"
                :src="$urlFor(image.asset).auto('format').width(700).url()"
                loading="lazy"
              />
            </div>
          </div>
        </div>
      </div>
  </div>
</template>

<script setup>
const bigger = ref(false);

const resize = (e) => {
  bigger.value = !bigger.value;
  var initHeight = 25.9;
  if (bigger.value == true) {
    const myInterval = setInterval(() => {
      initHeight += 2;
      const images = [...e.target.parentNode.children];
      const imageIndex = images.indexOf(e.target);
      const vwInPx = document.documentElement.clientWidth / 100;
      console.log(initHeight);
      e.target.parentNode.style.height = initHeight + "vw";
      e.target.parentNode.scrollBy(2.5 * vwInPx * imageIndex, 0);

      if (initHeight > 60) {
        clearInterval(myInterval);
      }
    }, 10);
  } else {
    initHeight = 61.9;
    const myInterval = setInterval(() => {
      initHeight -= 2;
      const images = [...e.target.parentNode.children];
      const imageIndex = images.indexOf(e.target);

      const vwInPx = document.documentElement.clientWidth / 100;
      console.log(initHeight);
      e.target.parentNode.style.height = initHeight + "vw";
      e.target.parentNode.scrollBy(-2.5 * vwInPx * imageIndex, 0);

      if (initHeight < 26.5) {
        clearInterval(myInterval);
        e.target.parentNode.style.height = "25.9vw";
      }
    }, 10);
  }
};

const query = groq`*[_type == "modelle"] {name, beschreibung, galerie, preis}`;
const { data: modelle, refresh } = useSanityQuery(query);

</script>

<style>
.galerie {
  margin-top: 1%;
  width: 100%;
  height: 25.9vw;
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
  aspect-ratio: 1 / 1;
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
  .galerie {
    height: 40vw;
  }
}
</style>
