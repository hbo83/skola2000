<template>
    <div class="documents">
        <v-row>
            <v-col cols="2">
      <h2>Dokumenty:</h2>
      <v-btn outlined text color="grey"  @click="showDocument('school')">
        Školní řád
      </v-btn>
      <v-btn outlined text color="grey" @click="showDocument('retinue')">
        Řád školní družiny
      </v-btn>
      <v-btn outlined text color="grey" @click="showDocument('eatery')">
        Řád školní jídelny
      </v-btn>
      <v-btn outlined text color="grey" @click="showDocument('orderOfKitchen')">
        Řád cvičné školní kuchyně
      </v-btn>
      <v-btn outlined text color="grey" @click="showDocument('orderOfWorkshop')">
        Řád školních dílen
      </v-btn>
      <v-btn outlined text color="grey" @click="showDocument('orderOfGym')">
        Řád tělocvičny
      </v-btn>
      <v-btn outlined text color="grey" @click="showDocument('orderOfPhysic')">
        Řád učebny fyziky
      </v-btn>
      <v-btn outlined text color="grey" @click="showDocument('orderOfMusic')">
        Řád učebny hudební výchovy
      </v-btn>
      <v-btn outlined text color="grey" @click="showDocument('orderOfChemie')">
        Řád učebny chemie
      </v-btn>
      <v-btn outlined text color="grey" @click="showDocument('orderOfNature')">
        Řád učebny přírodopisu
      </v-btn>
      <v-btn outlined text color="grey" @click="showDocument('orderOfIt')">
        Řád učebny výpočetní techniky
      </v-btn>
      <!-- <v-btn outlined text color="grey" @click="showDocument('school')">
        Konzultační hodiny
      </v-btn> -->
      <v-btn outlined text color="grey" @click="showDocument('absence')">
        Omlouvání žáků
      </v-btn>
      <!-- <v-btn outlined text color="grey" @click="showDocument('school')">
        Výroční zpráva
      </v-btn> -->
      <v-btn min-width="150" outlined text color="grey" @click="showDocument('gdpr')">
        GDPR
      </v-btn>
      </v-col>
      <v-col>
            <div class="text-center">
        <v-dialog v-model="dialog" width="1000">
          <template v-slot:activator="{ on }">
            <!-- <v-btn
          color="red lighten-2"
          dark
          v-on="on"
        >
          Click Me
            </v-btn>-->
          </template>

          <v-card>
            <v-card-title
              v-if="dialogContent === 'school'"
              class="headline grey lighten-2"
              primary-title
            >Školní řád</v-card-title>
            <v-card-title
              v-if="dialogContent === 'retinue'"
              class="headline grey lighten-2"
              primary-title
            >Řád školní družiny</v-card-title>
            <v-card-title
              v-if="dialogContent === 'eatery'"
              class="headline grey lighten-2"
              primary-title
            >Řád školní jídelny</v-card-title>
            <v-card-title
              v-if="dialogContent === 'teachersHour'"
              class="headline grey lighten-2"
              primary-title
            >Konzultační hodiny</v-card-title>
            <v-card-title
              v-if="dialogContent === 'orderOfKitchen'"
              class="headline grey lighten-2"
              primary-title
            >Řád cvičné školní kuchyně</v-card-title>
            <v-card-title
              v-if="dialogContent === 'orderOfWorkshop'"
              class="headline grey lighten-2"
              primary-title
            >Řád školních dílen</v-card-title>
            <v-card-title
              v-if="dialogContent === 'orderOfGym'"
              class="headline grey lighten-2"
              primary-title
            >Řád Tělocvičny</v-card-title>
            <v-card-title
              v-if="dialogContent === 'orderOfPhysic'"
              class="headline grey lighten-2"
              primary-title
            >Řád učebny Fyziky</v-card-title>
            <v-card-title
              v-if="dialogContent === 'orderOfMusic'"
              class="headline grey lighten-2"
              primary-title
            >Řád učebny hudební výchovy</v-card-title>
            <v-card-title
              v-if="dialogContent === 'orderOfChemie'"
              class="headline grey lighten-2"
              primary-title
            >Řád učebny chemie</v-card-title>
            <v-card-title
              v-if="dialogContent === 'orderOfNature'"
              class="headline grey lighten-2"
              primary-title
            >Řád učebny přírodopisu</v-card-title>
            <v-card-title
              v-if="dialogContent === 'orderOfIt'"
              class="headline grey lighten-2"
              primary-title
            >Řád učebny výpočetní techniky</v-card-title>
            <v-card-title
              v-if="dialogContent === 'absence'"
              class="headline grey lighten-2"
              primary-title
            >Omlouvání žáků</v-card-title>
            <v-card-title
              v-if="dialogContent === 'gdpr'"
              class="headline grey lighten-2"
              primary-title
            >GDPR</v-card-title>

            <v-card-text>
              <SkolniRad v-if="dialogContent === 'school'" />
              <DruzinaRad v-if="dialogContent === 'retinue'" />
              <JidelnaRad v-if="dialogContent === 'eatery'" />
              <KonzultacniHodiny v-if="dialogContent === 'teachersHour'" />
              <RadCvicneSkolniKuchyne v-if="dialogContent === 'orderOfKitchen'" />
              <RadSkolnichDilen v-if="dialogContent === 'orderOfWorkshop'" />
              <RadTelocvicny v-if="dialogContent === 'orderOfGym'" />
              <RadUcebnyFyziky v-if="dialogContent === 'orderOfPhysic'" />
              <RadUcebnyHudebniVychovy v-if="dialogContent === 'orderOfMusic'" />
              <RadUcebnyChemie v-if="dialogContent === 'orderOfChemie'" />
              <RadUcebnyPrirodopisu v-if="dialogContent === 'orderOfNature'" />
              <RadUcebnyVypocetniTechniky v-if="dialogContent === 'orderOfIt'" />
              <Gdpr v-if="dialogContent === 'gdpr'" />
              <Absence v-if="dialogContent === 'absence'" />
            </v-card-text>

            <v-divider></v-divider>

            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="primary" text @click="dialog = false">Rozumím</v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </div>
      </v-col>
        </v-row>
    </div>
</template>

<script>
import SkolniRad from "@/components/documents/SkolniRad.vue";
import DruzinaRad from "@/components/documents/DruzinaRad.vue";
import JidelnaRad from "@/components/documents/JidelnaRad.vue";
import KonzultacniHodiny from "@/components/documents/KonzultacniHodiny.vue";
import RadCvicneSkolniKuchyne from "@/components/documents/RadCvicneSkolniKuchyne.vue";
import RadSkolnichDilen from "@/components/documents/RadSkolnichDilen.vue";
import RadTelocvicny from "@/components/documents/RadTelocvicny.vue";
import RadUcebnyFyziky from "@/components/documents/RadUcebnyFyziky.vue";
import RadUcebnyHudebniVychovy from "@/components/documents/RadUcebnyHudebniVychovy.vue";
import RadUcebnyChemie from "@/components/documents/RadUcebnyChemie.vue";
import RadUcebnyPrirodopisu from "@/components/documents/RadUcebnyPrirodopisu.vue";
import RadUcebnyVypocetniTechniky from "@/components/documents/RadUcebnyVypocetniTechniky.vue";
import Gdpr from '@/components/documents/GDPR.vue'
import Absence from '@/components/documents/Absence.vue'
export default {
    name: 'Documents',
    components: {
        SkolniRad,
    DruzinaRad,
    JidelnaRad,
    KonzultacniHodiny,
    RadCvicneSkolniKuchyne,
    RadSkolnichDilen,
    RadTelocvicny,
    RadUcebnyFyziky,
    RadUcebnyHudebniVychovy,
    RadUcebnyChemie,
    RadUcebnyPrirodopisu,
    RadUcebnyVypocetniTechniky,
    Absence,
    Gdpr
    },
      data() {
    return {
      dialog: false,
      dialogContent: ""
    };
  },
  methods: {
    showDocument(content) {
      this.dialog = true;
      this.dialogContent = content;
    },
    download() {
      window.open("../../assets/prihlaska.pdf");
    }
  }
}
</script>
<style scoped>
.documents {
    /* background-color: pink; */
    width: 100%;
    height: 50px;
}
</style>