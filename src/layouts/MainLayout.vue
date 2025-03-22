<template>
  <div class="q-pa-sm">
    <q-layout view="hHh Lpr lff">
      <q-header :class="$q.dark.isActive ? 'bg-secondary' : 'bg-white'" style="height: 100px">
        <q-toolbar class="q-pl-lg q-pb-sm"  style="height: 100px">
          <img src="https://static.wixstatic.com/media/65c703_d6cca897e9b244f188ab20f8f5ac193f~mv2.png/v1/fill/w_124,h_100,al_c,q_85,usm_0.66_1.00_0.01,enc_avif,quality_auto/Untitled.png" class="q-mt-md q-pb-none" style="width: 80px"/>
          <q-toolbar-title class="text-h6 text-grey-9 q-mt-xl q-pl-md">Willkommen auf der LuMia kreativ Produktseite</q-toolbar-title>
          <q-btn flat round dense icon="language" color="grey-9" class="q-mt-xl q-pl-md"/>
          <q-btn flat round dense icon="phone" color="grey-9" class="q-mt-xl q-pl-md" />
          <q-btn flat round dense icon="mail" color="grey-9" class="q-mt-xl q-pl-md" />
        </q-toolbar>
      </q-header>
      <q-drawer
        v-model="drawer"
        show-if-above
        :width="200"
        :breakpoint="500"
        bordered
        :class="$q.dark.isActive ? 'bg-grey-9' : 'bg-grey-3'"
      >
        <q-scroll-area class="fit">
          <q-list>

            <template v-for="(menuItem, index) in menuList" :key="index">
              <q-item clickable :active="menuItem.label === 'Outbox'" v-ripple>
                <q-item-section>
                  {{ menuItem.label }}
                </q-item-section>
              </q-item>
              <q-separator :key="'sep' + index"  v-if="menuItem.separator" />
            </template>

          </q-list>
        </q-scroll-area>
      </q-drawer>

      <q-page-container>
        <router-view />
      </q-page-container>

      
            <q-footer class="bg-grey-3">
        <q-toolbar>
          <q-toolbar-title class="text-caption text-grey-9 text-right">Raaf und Hochstatter GbR I Pfarrgasse 6 I 73460 Hüttlingen</q-toolbar-title>
        </q-toolbar>
      </q-footer>
    </q-layout>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const drawer = ref(false)
const menuList = [
  {
    label: 'Neuheiten',
    separator: true
  },
  {
    label: 'Betonformen',
    separator: false
  },
  {
    label: 'Türkränze',
    separator: true
  },
  {
    label: 'Hochzeit',
    separator: false
  },
  {
    label: 'Kinder (Geburt, Geburtstag, Taufe)',
    separator: false
  },
  {
    label: 'Geburtstag',
    separator: false
  },
    {
    label: 'Sets zu verschiedenen Anlässen',
    separator: true
  },
    {
    label: 'Frühling/Ostern',
    separator: false
  },
    {
    label: 'Herbst',
    separator: false
  },
    {
    label: 'Winter/Weihnachten',
  },
]


</script>