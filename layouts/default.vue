<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
      color="red"
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title v-text="title" />

      <v-spacer />
      <v-btn
        icon
        to="parlament"
      >
        <v-icon>mdi-tie</v-icon>
      </v-btn>
      <v-btn
        icon
        @click.stop="miniVariant = !miniVariant"
      >
        <v-icon>mdi-package-variant-closed</v-icon>
      </v-btn>
      <v-btn
        icon
        @click.stop="miniVariant = !miniVariant"
      >
        <v-icon>mdi-panorama-wide-angle</v-icon>
      </v-btn>
      <v-btn
        icon
        @click.stop="miniVariant = !miniVariant"
      >
        <v-icon>mdi-email</v-icon>
      </v-btn>
      <v-btn
        icon
        @click.stop="miniVariant = !miniVariant"
      >
        <v-icon>mdi-hexagon-outline</v-icon>
      </v-btn>

    </v-app-bar>
    <div class="subNav" style="width: 100%; height: 50px; margin: 80px 0 0 50px;">
      
       <v-btn
        icon
        to="school"
      >
        <v-icon>mdi-city</v-icon>
      </v-btn>
      <v-btn
        icon
        to="retinue"
      >
        <v-icon>mdi-panda</v-icon>
      </v-btn>
      <v-btn
        icon
        to="eatery"
      >
        <v-icon>mdi-silverware-variant</v-icon>
      </v-btn>
      <v-btn
        icon
        to="workshop"
      >
        <v-icon>mdi-magnet</v-icon>
      </v-btn>
    </div>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
   
    <v-footer
      :fixed="fixed"
      app
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      miniVariant: false,
      right: true,
      
      title: 'Základní škola Úšovice Mariánské Lázně'
    }
  }
}
</script>
