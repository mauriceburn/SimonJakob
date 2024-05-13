<template>
    <div>
        <div class="modal" v-if="anzeige.beschreibung">
            <SanityContent :blocks="anzeige.beschreibung" :serializers="serializers" />
        </div>
    </div>
</template>

<script setup>
import CenterBlock from "~/components/CenterBlock.vue";
import ImageBlock from "~~/components/ImageBlock.vue";

const props = defineProps({
    anzeige: {},
});

const serializers = {
    importedComponent: CenterBlock,
    styles: {
        center: CenterBlock,
    },
    types: {
        image: ImageBlock,
    },
};
</script>

<style>
.modal {
    position: absolute;
    width: 89%;
    z-index: 1;
    text-align: center;
}
</style>