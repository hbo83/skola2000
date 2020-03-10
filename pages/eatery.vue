<template>
  <v-layout>
    <v-flex class="text-center">
        <h1>Jídelna</h1>
        <p>Otevřeno od 12.00 do 14.00</p>
       
    <v-card class="my-10">
      <v-data-table
        :headers="headers"
        :items="food"
        :items-per-page="5"
        class="elevation-1"
        disable-filtering
        disable-pagination
        disable-sort
        hide-default-footer
      ></v-data-table>
    </v-card>
    <v-card>
      <v-expansion-panels>
        <v-expansion-panel v-for="(item, i) in content" :key="i">
          <v-expansion-panel-header>
            <p>
              <v-icon>{{item.icon.home}}</v-icon>
              <span style="text-align: left">{{ item.header }}</span>
            </p>
          </v-expansion-panel-header>
          <v-expansion-panel-content>
            <p>
              <v-icon>{{item.icon.child}}</v-icon>
              <span style="text-align: left">{{ item.content.n1 }}</span>
            </p>
            <p>
              <v-icon>{{item.icon.child}}</v-icon>
              <span style="text-align: left">{{ item.content.n2 }}</span>
            </p>
            <p>
              <v-icon>{{item.icon.child}}</v-icon>
              <span style="text-align: left">{{ item.content.n3 }}</span>
            </p>
            <p>
              <v-icon>{{item.icon.adult}}</v-icon>
              <span style="text-align: left">{{ item.content.n4 }}</span>
            </p>
            <p>
              <span style="text-align: left">{{ item.content.n5 }}</span>
            </p>
            <p>
              <span style="text-align: left">{{ item.content.n6 }}</span>
            </p>
          </v-expansion-panel-content>
        </v-expansion-panel>
      </v-expansion-panels>
    </v-card>
    <br />
    <h3>Alergeny:</h3>
    <span style="color: red">
      <b>1</b>
    </span>
    <span>Lepek |</span>
    <span style="color: green; margin-left: 10px;">2</span>
    <span>Korýši |</span>
    <span style="color: blue; margin-left: 10px;">3</span>
    <span>Vejce |</span>
    <span style="color: yellow; margin-left: 10px;">4</span>
    <span>Ryby |</span>
    <span style="color: purple; margin-left: 10px;">5</span>
    <span>Arašídy |</span>
    <span style="color: pink; margin-left: 10px;">6</span>
    <span>Soja |</span>
    <span style="color: lime; margin-left: 10px;">7</span>
    <span>Mléko |</span>
    <span style="color: brown; margin-left: 10px;">8</span>
    <span>Ořechy |</span>
    <span style="color: teal; margin-left: 10px;">9</span>
    <span>Celer |</span>
    <span style="color: cyan; margin-left: 10px;">10</span>
    <span>Hořčice |</span>
    <span style="color: #e995d3; margin-left: 10px;">11</span>
    <span>Sezam |</span>
    <span style="color: orange; margin-left: 10px;">12</span>
    <span>Siřičitany |</span>
    <span style="color: #8c4e82; margin-left: 10px;">13</span>
    <span>Lupinak |</span>
    <span style="color: #0c946e; margin-left: 10px;">14</span>
    <span>Měkkýši</span>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  name: "EateryInfo",
  components: {},
  data() {
    return {
      foodContent: {
        days: ["Pondělí", "Úterý", "Středa", "Čtvrtek", "Pátek"]
      },
      headers: [
        {
          text: "9. března – 13. března 2020",
          align: "left",
          sortable: false,
          value: "name"
        },
        { text: "Polévka", value: "soup" },
        { text: "Hlavní jídlo", value: "main" },
        { text: "Dezert/ovoce", value: "desert" },
        { text: "Nápoj", value: "drink" },
        { text: "Alergeny", value: "allergen" }
      ],
      food: [
        {
          name: "Pondělí",
          soup: "Polévka brokolicová",
          main: "Vepřové kostky s vejci, brambor, zelný salát",
          // desert: "Ovoce,",
          drink: "Vitamínový nápoj/minerálka",
          allergen: "01, 03, 06, 07, 09"
        },
        {
          name: "Úterý",
          soup: "Polévka vývar s vlasovými nudlemi",
          main: "Svíčková na smetaně, houskový knedlík",
          // desert: "Šlehaný tvaroh s müsli",
          drink: "Ovoce, sirup/minerálka",
          allergen: "01, 03, 07, 09, 10"
        },
        {
          name: "Středa",
          soup: "Polévka čočková se zeleninou",
          main: "Smažené rybí filé, bramborová kaše, kompot",
          // desert: "Mrkvový salát s jablky",
          drink: "Carotela/minerálka",
          allergen: "01, 03, 04, 07, 09"
        },
        {
          name: "Čtvrtek",
          soup: "Polévka gulášová",
          main: "Bramborové šišky s mákem",
          desert: "Ovoce",
          drink: "ochucené mléko/sirup/ minerálka",
          allergen: "01, 03, 06, 07, 08"
        },
        {
          name: "Pátek",
          soup: "Polévka drožďová",
          main: "Rizoto s drůbežím masem, sýr, kyselá okurka",
          // desert: "kompot",
          drink: "Džus/minerálka",
          allergen: "01, 03, 07, 09, 10"
        }
      ],
      content: [
        {
          header: "Stravné",
          icon: {
            home: "mdi-coin",
            child: "mdi-human-child",
            adult: "mdi-human-male-female"
          },
          content: {
            n1: "Žáci 6 - 10 let 20 .-Kč",
            n2: "Žáci 11 - 14 let 22 .-Kč",
            n3: "Žáci 15 a více let 25 .-Kč",
            n4: "Dospělí 32.-Kč"
          }
        },
        {
          header: "Informace zákonným zástupcům",
          icon: {
            home: "mdi-information-outline",
            child: "",
            adult: ""
          },
          content: {
            n1:
              "1. Příspěvky na stravování s platností od 1. 1. 2016 Kategorie 7 – 10 let 20,- Kč Kategorie 11 – 15 let 22,- Kč Kategorie 15 – 18 let 25,- Kč Bezkontaktní čip (9 let záruka) 117,-Kč",
            n2:
              "2. Stravování je poskytováno na základě vyplněné PŘIHLÁŠKY KE STRAVOVÁNÍ, která je platná na ten daný školní rok.",
            n3:
              "3. Příspěvky za stravování na následující měsíc, musí být uhrazeny nejpozději do posledního dne v daném měsíci.",
            n4:
              "4. Oběd je vydánbna základě stávající platné identifikační karty, nebo bezkontaktního čipu. V případě ztráty nebo poškození, lze zakoupit nový čip (částka se připočítává k platbě za stravování)",
            n5:
              "5. Bez platné identifikační karty nebo bezkontaktního čipu NEBUDE OBĚD VYDÁN!",
            n6:
              "6. Úhrady poplatků za obědy lze provádět: a) trvalým příkazem na účet: KB 6030331/0100 ( ve ŠJ Vám bude sdělen variabilní symbol Vašeho dítěte a částka, přeplatky budou 2" +
              "x ročně vyúčtovány a vráceny na Váš účet) b) příkazem k inkasu – je nutné dát svolení k inkasu na účet KB 6030331/0100 (přeplatky stravného se odečítají ihned následující měsíc) c) hotově (jen ve výjimečných" +
              "případech) Platba poštovní poukázkou byla zrušena 7. V případě nepřítomnosti žáka ve škole jsou rodiče povinni oběd odhlásit nejpozději do 8 hodin ráno na daný den – osobně, telefonicky na číslo ŠJ 354 623" +
              "557 nebo na e-mail: jídelna@zsml2.cz Oběd do„jídlonosiče“může být vydán pouze 1. den nepřítomnosti od 11.30 – 12,00 8. V případě ukončení stravování jsou zákonní zástupci povinni tuto skutečnost oznámit ve" +
              "školní jídelně. 9. ŠJ zabezpečuje stravování žáků v době vyučování a jejich přítomnosti ve škole. 10. Další informace naleznete ve Vnitřním řádu školní jídelny. 11. Žáci mají přístup do ŠJ pouze za přítomnosti" +
              "pedagoga vykonávajícího dohled. 12. Ve ŠJ se žáci chovají ukázněně, udržují pořádek a řídí se pokyny dohledu. 13. Pokud platby za stravné neproběhnou v řádném termínu, může být žák ze stravování vyloučen Výdej" +
              "obědů žákům: 12:00 – 14:00 hodin Za ŠJ : Zdeňka Portová, vedoucí školní jídelny Přihlášky na stravné si vyzvedněte ve ŠJ nebo na stránkách školy"
          }
        },
        
      ]
    };
  }
};
</script>
<style scoped>
.eateryContent {
  /* margin-top: 50px; */
}
</style>

