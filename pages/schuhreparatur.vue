<template>
  <div>
    <div v-if="site" class="home">
      <div class="title">
        <h1>{{ site.title }}</h1>
      </div>
      <div class="line"></div>
      <div class="content">
        <SanityContent :blocks="site.beschreibung" />
      </div>
      <div class="links">
        <NuxtLink
          v-for="(link, index) in site.links"
          :key="index"
          :to="'/' + link.siteLink"
        >
          <SiteLinks :linkData="link" />
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<script setup>
import CenterBlock from "~/components/CenterBlock.vue";

const query = groq`*[_type == "seiten" && linkName == "schuhreparatur"][0]`;
const { data: site } = useSanityQuery(query);

const serializers = {
  importedComponent: CenterBlock,
  styles: {
    center: CenterBlock,
  },
};
</script>
