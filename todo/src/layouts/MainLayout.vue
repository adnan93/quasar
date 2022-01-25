<template>
  <q-layout view="lHh Lpr lFf">
    <q-header >
      <q-toolbar>
        <q-btn
           flat
           dense
           round
           @click="leftDrawerOpen =!leftDrawerOpen"
           icon="menu" 
           aria-label="Menu" 
           />
      </q-toolbar>

      <div class="q-px-lg q-pt-lg q-mb-lg">
        <div class="text-h3">Todo</div>
        <div class="subtitle1">{{ toDaysDate }}</div>
      </div>

      <!-- <q-img src="../assets/mountain.jpg" 
      class="absolute-top header-image" />  -->
    </q-header>

    <q-drawer
     v-model="leftDrawerOpen"
        show-if-above
        :width="250"
        :breakpoint="600">
      <q-scroll-area
        style="
          height: calc(100% - 150px);
          margin-top: 150px;
          border-right: 1px solid #ddd;"
      >
        <q-list padding>
          <q-item to="/" clickable v-ripple exact>
            <q-item-section avatar>
              <q-icon name="list" />
            </q-item-section>

            <q-item-section> Todo </q-item-section>
          </q-item>

          <q-item to="/help" clickable v-ripple exact>
            <q-item-section avatar>
              <q-icon name="help" />
            </q-item-section>

            <q-item-section> Help </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>

      <q-img class="absolute-top" src="../assets/mountain.jpg" style="height: 192">
        <div class="absolute-bottom bg-transparent">
          <q-avatar size="56px" class="q-mb-sm">
            <img src="https://cdn.quasar.dev/img/boy-avatar.png" />
          </q-avatar>
          <div class="text-weight-bold">Adnan barbar</div>
          <div>adnan.syria.91@gmail.com</div>
        </div>
      </q-img>
    </q-drawer>

    <q-page-container>
      <keep-alive>
        <router-view />
      </keep-alive>
    </q-page-container>
  </q-layout>
</template>

<script>
import { date } from "quasar";



import {  ref } from "vue";

export default {
  name: "MainLayout",
  data(){
    return {
      leftDrawerOpen : false,
    }

  },

  computed: {
    toDaysDate() {
      let timeStamp = Date.now();
      return date.formatDate(timeStamp, "ddd D MMM ");
    },
  },
};
</script>

<style lang="scss">
.header-image {
  height: 100%;
  opacity: 0.5;
  filter: grayscale(100%);
}
</style>
