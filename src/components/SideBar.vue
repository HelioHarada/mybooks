<template>
  <div>
    <!-- top avatar img -->
    <avatar-perfil />
    <q-list padding>
      <menu-link v-for="item in links" :key="item.title" v-bind="item" />
      <!-- <q-item clickable v-ripple :to="{path : 'mybooks'}" >
        <q-item-section avatar>
          <q-icon name="inbox" />
        </q-item-section>
        <q-item-section>
          Meus Livros
        </q-item-section>
      </q-item> -->
    </q-list>
  </div>
</template>

<script>
import Avatar from 'components/sidebar/Avatar'
import Link from 'components/sidebar/Links'
export default {
  name: 'SideBar',
  components: {
    'avatar-perfil': Avatar,
    'menu-link': Link
  },
  data () {
    return {
      links: [
        {
          title: 'Home',
          router: '/',
          icon: 'home'
        },
        {
          title: 'Meus Livros',
          router: 'mybooks',
          icon: 'inbox'
        }
      ]
    }
  }
}
</script>
