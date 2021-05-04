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
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title>
          Gerenciamento de Produtos
        </q-toolbar-title>

        <div></div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-1"
    >
      <q-list>
        <q-item-label
          header
          class="text-grey-8"
        >
          Menu
        </q-item-label>
        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
          v-ripple
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <transition
        name="transitions"
        enter-active-class="animated slideInRight"
        leave-active-class="animated fadeOut"
        mode="out-in"
      >
        <router-view class="layout-view"></router-view>
      </transition>
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'

const linksData = [
  {
    title: 'Home',
    caption: 'Home',
    icon: 'home',
    link: '/'
  },
  {
    title: 'Login',
    caption: 'Login',
    icon: 'person',
    link: '/login'
  },
  {
    title: 'Produto',
    caption: 'Produto',
    icon: 'code',
    link: '/Produto'
  }
];

export default {
  name: 'MainLayout',
  components: { EssentialLink },
  data () {
    return {
      leftDrawerOpen: false,
      essentialLinks: linksData
    }
  }
}
</script>
