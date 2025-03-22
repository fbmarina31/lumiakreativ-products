<template>
  <q-page padding>
    <q-banner class="text-grey-9 bg-white text-center">
      Du bist auf der Suche nach einer Kleinigkeit für dich oder zum verschenken? Dann wirst du
      hoffentlich bei uns fündig.<br />
      Gerne erstellen und personalisieren wir auch etwas nach deinen Wünschen. <br />Melde Dich
      gerne bei uns über die oben rechts aufgezeigten Kontaktmöglichkeiten.
    </q-banner>
    <div class="q-pa-md row items-start q-gutter-md">
      <q-card
        flat
        bordered
        style="width: 300px; height: 550px"
        v-for="product in products"
        :key="product.id"
      >
        <img :src="product.image" />
        <q-list>
          <q-item-section>
            <q-item-label class="text-h5 bg-grey-3 q-pa-xs text-center">{{
              product.title
            }}</q-item-label>
            <div class="row q-pa-xs q-mt-sm">
              <div class="q-px-xs">Nr.</div>
              <div class="q-px-xs text-weight-bold">{{ product.id }}</div>
            </div>
            <div class="row q-pa-xs">
              <div class="q-px-xs">Preis</div>
              <div class="q-px-xs text-weight-bold">{{ product.price }} €</div>
            </div>
            <div class="row q-pa-xs">
              <div class="q-px-xs">Maße</div>
              <div class="q-px-xs text-weight-bold">{{ product.size }}</div>
            </div>
            <div class="row q-pa-xs">
              <div class="q-px-xs">Beschreibung</div>
              <div class="q-px-xs text-weight-bold">
                {{ product.description }}
              </div>
            </div>
          </q-item-section>
        </q-list>
      </q-card>
    </div>
  </q-page>
</template>

<script setup lang="ts">
import { onMounted, ref } from 'vue';

interface Product {
  id: number;
  title: string;
  price: number;
  size: string;
  description: string;
  image: string;
  categories: string[];
}

const products = ref<Product[]>([]);

onMounted(async () => {
  await fetch('./products.json')
    .then((response) => response.json())
    .then((data) => {
      products.value = data;
    });
});
</script>
