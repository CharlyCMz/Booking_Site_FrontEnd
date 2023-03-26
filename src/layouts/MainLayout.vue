<template>
  <q-layout view="hHh Lpr lff">
    <q-header elevated>
      <q-toolbar>
        <q-btn flat dense round icon="menu" aria-label="Menu" @click="toggleLeftDrawer" />

        <q-toolbar-title class="text-bold row items-center q-pa-md q-gutter-sm">
          <img src="../../public/icons/favicon-96x96.png" alt="Project Logo" style="width: 36px; height: 36px">
          <div>
            Chuck Booking Site
          </div>
        </q-toolbar-title>

        <div class="q-pa-md q-gutter-sm">
          <q-btn color="accent" icon-right="how_to_reg" label="Sign Up" />
          <q-btn color="secondary" icon-right="login" label="Login" />
          <q-btn color="secondary" icon-right="logout" label="Logout" />
        </div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" :width="200" :breakpoint="500" overlay bordered class="bg-grey-3">
      <q-img class="absolute-top" src="https://cdn.quasar.dev/img/material.png" style="height: 150px">
        <div class="absolute-bottom bg-transparent">
          <q-avatar size="40px" class="q-mb-sm">
            <img src="https://cdn.quasar.dev/img/boy-avatar.png">
          </q-avatar>
          <div class="text-weight-bold">Charly Correa M.</div>
          <div>@CharlyCMz</div>
        </div>
      </q-img>
      <q-scroll-area style="height: calc(100% - 150px); margin-top: 150px; border-right: 1px solid #ddd">
        <q-list>

          <template v-for="(menuItem, index) in menuList" :key="index">
            <q-item clickable :active="menuItem.label === 'Outbox'" v-ripple>
              <q-item-section avatar>
                <q-icon :name="menuItem.icon" />
              </q-item-section>
              <q-item-section>
                {{ menuItem.label }}
              </q-item-section>
            </q-item>
            <q-separator :key="'sep' + index" v-if="menuItem.separator" />
          </template>

        </q-list>
      </q-scroll-area>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
    <q-footer class="bg-indigo-1 text-black">
      <q-toolbar class="justify-center">
        <div>
          <div>Copyright © Booking Site 2023 by CharlyCMz</div>
          <div class="footer-icons">
            <a href="https://www.linkedin.com/in/charlycmz/" target="blank" style="height: 25px;">
              <q-icon name="img:../../public/icons/linkedin-icon.svg" size="25px" />
            </a>
            <a href="https://github.com/CharlyCMz" target="blank" style="height: 20px;">
              <q-icon name="img:../../public/icons/github-icon.svg" size="20px" />
            </a>
            <a href="https://www.instagram.com/charlycm.91/" target="blank" style="height: 20px;">
              <q-icon name="img:../../public/icons/instagram-icon.svg" size="20px" />
            </a>
          </div>
        </div>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'

const menuList = [
  {
    icon: 'home',
    label: 'Home',
    separator: true
  },
  {
    icon: 'send',
    label: 'Messages',
    separator: false
  },
  {
    icon: 'event_available',
    label: 'My Bookings',
    separator: true
  },
  {
    icon: 'settings',
    label: 'Settings',
    separator: false
  },
  {
    icon: 'feedback',
    label: 'Send Feedback',
    separator: false
  },
  {
    icon: 'help',
    iconColor: 'primary',
    label: 'Help',
    separator: false
  }
]

export default defineComponent({
  name: 'MainLayout',

  components: {

  },

  setup() {
    const leftDrawerOpen = ref(false)

    return {
      menuList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>

<style>
.footer-icons {
  display: flex;
  justify-content: center;
}

.footer-icons a {
  padding-left: 8px;
}
</style>
