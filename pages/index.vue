<template>
  <div class="home">
    <SanityContent :blocks="site.beschreibung" />
    <NuxtLink v-for="(link, index) in site.links" :key="index" :to="'/' + link.siteLink">
      <SiteLinks
        :bgImage="link.asset._ref"
        :ovImage="link.overlay.asset._ref"
      />
    </NuxtLink>
  </div>
</template>

<script setup>
const query = groq`*[_type == "seiten" && name == "startseite"][0]`;
const { data: site, refresh } = useSanityQuery(query);
</script>

<style>
.home {
  display: flex;
  gap: 7%;
  justify-content: space-between;
  padding: 0 2.5% 0 2.5%;
}

.right {
  width: 40%;
}

.right img {
  width: 100%;
}
</style>
