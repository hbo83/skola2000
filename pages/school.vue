<template>
  <v-layout>
    <v-flex class="text-center">
      <!-- dam tam prepinace kterej prepne ikony na velky text pro slabozrake -->
      <h1>O škole</h1>
      <p>
        K 1. 1. 2008 byly sloučeny dvě základní školy (ZŠ Školní náměstí a ZŠ Ruská) v jeden subjekt ZŠ, Mariánské Lázně, Ruská 355,
        příspěvková organizace. Zařízení bylo umístěno celkem ve třech budovách. Přesunutí všech žáků do Úšovic bylo dokončeno na začátku
        olního roku 2009/2010.
        Dne 1.11.2009 byl změněn název školy na Základní škola Úšovice, Mariánské Lázně, Školní náměstí 472, příspěvková organizace.
      </p>
      <h2>Základní škola Úšovice, Mariánské Lázně, Školní náměstí 472, příspěvková organizace</h2>
      <h3>Školní náměstí 472/3, 353 01 Mariánské Lázně</h3>
      <p>Ředitel školy: Mgr. Monika Preňková</p>
      <p>Zástupce ředitele: Mgr. Věra Kučavová a Mgr. Vlasta Matysová</p>
      <p>Zřizovatel školy: Město Mariánské Lázně, Ruská 155/3, 353 01</p>
      <p>Telefon: Základní škola 354 624 654, Základní škola pobočka 354 622 860, Družina	+420 354 625 634</p>
      <p>Elektronická adresa: sekretariát@zsusovice.cz</p>
      <p>Datová schránka: wkkmpmx</p>
      <v-row>
        <v-col>
          <h3>Projekty</h3>
        </v-col>
      </v-row>
      <v-row justify="start">
        
      <v-col>
        <iframe allowfullscreen="" frameborder="0" height="300" src="https://www.google.com/maps/embed?pb=!1m14!1m8!1m3!1d5943.156307202728!2d12.708357!3d49.952802!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0xb76b6392ba8fcc21!2zWsOha2xhZG7DrSDFoWtvbGEgw5rFoW92aWNlLCBNYXJpw6Fuc2vDqSBMw6F6bsSbLCDFoGtvbG7DrSBuw6FtxJtzdMOtIDQ3MiwgcMWZw61zcMSbdmtvdsOhIG9yZ2FuaXphY2U!5e1!3m2!1scs!2sus!4v1544524727784" style="border:0" width="400"></iframe>
      </v-col>
      <v-col>
        <iframe class="kb-widget" frameborder="0" height="430" id="kb-widget-transparent-account" src="https://www.kb.cz/cs/transparentni-ucty/widget/140765670-zs-usovice-ml-skolni-nam-472-po/detail-uctu-1154310390217.shtml" width="320" scrolling="no" style="overflow: hidden;"></iframe>
      </v-col>
      </v-row>
     <v-row>
       <v-col>
         <Sponsors />
       </v-col>
     </v-row>
    </v-flex>
  </v-layout>
</template>

<script>
import Sponsors from '@/components/Sponsors.vue'
export default {
  components: {
    Sponsors
  }
}
</script>