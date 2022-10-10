<template>
  <div>
    <div v-if="site">
      <Head>
        <Meta name="description" content="Der Beruf des Schuhmachers geht auf meinen Grossvater mütterlicherseits zurück. Bis mein Vater 1968 aus Midyat/Türkei in die Schweiz kam, stellte er in der Türkei Massschuhe her. Damals wurden in der Türkei die Schuhe noch beim Schuhmacher bestellt." />
      </Head>
    
      <div v-if="site">
        <div class="content" v-if="site.beschreibung">
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
  </div>
</template>

<script setup>
import CenterBlock from "~/components/CenterBlock.vue";

const query = groq`*[_id == "83df670e-43f2-414e-b386-555ebff8cfce"][0]`;
const { data: site, refresh } = useSanityQuery(query);


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

@media screen and (max-width: 900px) {
  .links {
    display: block;
  }

  .container {
    margin-bottom: 10%;
  }
}
</style>
