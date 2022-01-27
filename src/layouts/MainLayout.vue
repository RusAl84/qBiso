<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />
          <img  
    alt="hedgehog"
    src="~assets/hedgehog.png" 
    style="width: 40px; height: 40px"/>
        <q-toolbar-title>
          Ёж мессенджер
        </q-toolbar-title>
        <q-btn
          flat
          dense
          round
          icon="login"
          aria-label="Menu"
          @click="prompt = true"
        />
        <div>  v 1.0</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
    >
      <q-list>
        <q-item-label
          header
        >
          Ссылки
        </q-item-label>

        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
     <q-dialog v-model="prompt" persistent>
      <q-card style="min-width: 350px">
        <q-card-section>
          <div class="text-h6">Введите своё имя:</div>
        </q-card-section>

        <q-card-section class="q-pt-none">
          <q-input dense v-model="userName" autofocus @keyup.enter="prompt = false" />
        </q-card-section>

        <q-card-actions align="right" class="text-primary">
          <q-btn flat label="Cancel" @click="cancelBth" v-close-popup />
          <q-btn flat label="Ok"  v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Главная',
    icon: 'school',
    link: '/'
  },

  {
    title: 'О проекте',
    icon: 'chat',
    link: '/about'
  },
 
];

import { defineComponent, ref, computed } from 'vue'
import { useStore } from 'vuex'


export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  setup () {
    const leftDrawerOpen = ref(false)
    const $store = useStore()
    let userName = computed({
      get: ()=> $store.state.ezh.userName,
      set: val => {
        $store.commit('ezh/updateUserName', val)
      }
    })
    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      },
      prompt: ref(false),
      $store,
      userName,
    }
  },
  methods:{
  cancelBth(){
    this.userName=""
  },}
})
</script>
