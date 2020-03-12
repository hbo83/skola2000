<template>
  <v-container class="">
    <v-row no-gutters>
      <v-col>
        <News />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import News from '@/components/News.vue'
export default {
  components: {
     News
  }
}
</script>
