<template>
  <v-container class="">
    <v-row no-gutters>
      <v-col>
        <Documents />
        
        
      </v-col>
    </v-row>
    <v-row>
        <v-col>
    <!-- <nuxt-link to="/documents">About (internal link that belongs to the Nuxt App)</nuxt-link> -->
        </v-col>
    </v-row>
    <!-- <router-view></router-view> -->
  </v-container>
  
</template>

<script>
import Documents from '@/components/Documents.vue'
export default {
  components: {
     Documents
  },
  methods: {
     
      }
  }

</script>
