<template>
  <div>
      <div v-if="site">
        <Head>
          <Title>{{site.name}}</Title>
          <Meta name="description" :content="site.beschreibung[0].children[0].text" />
        </Head>
        <div v-if="site" class="home">
          <div class="title">
            <h1>{{ site.title }}</h1>
          </div>
          <div class="line"></div>
          <div class="content" v-if="site.beschreibung">
            <SanityContent :blocks="site.beschreibung" :serializers="serializers" />
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
  </div>
</template>

<script setup>
import CenterBlock from "~/components/CenterBlock.vue";
import ImageBlock from "~~/components/ImageBlock.vue";

const query = groq`*[_type == "seiten" && linkName == "kontakt"][0]`;
const { data: site, refresh } = useSanityQuery(query);


const serializers = {
  importedComponent: CenterBlock,
  styles: {
    center: CenterBlock,
  },
  types: {
    image: ImageBlock
  }
};
</script>
