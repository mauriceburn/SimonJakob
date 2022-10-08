<template>
  <div>
    <div v-if="site">
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

const query = groq`*[_id == "83df670e-43f2-414e-b386-555ebff8cfce"][0]`;
const { data: site } = useSanityQuery(query);
const serializers = {
  importedComponent: CenterBlock,
  styles: {
    center: CenterBlock,
  },
};
</script>

<style>
.links {
  display: flex;
  gap: 7%;
  justify-content: space-between;
  padding: 0 2.5% 0 2.5%;
}
</style>
