<template>
  <div class="actionsContent">
    <v-row>
      <v-col cols="9">
        <h1 style="color: #90caf9">Akce školy</h1>
        <hr />

        <template>
          <div>
            <v-sheet tile height="54" color="grey lighten-3" class="d-flex">
              <v-btn icon class="ma-2" @click="$refs.calendar.prev()">
                <v-icon>mdi-chevron-left</v-icon>
              </v-btn>
              <v-select
                v-model="type"
                :items="types"
                dense
                outlined
                hide-details
                class="ma-2"
                label="zobrazení"
              ></v-select>
              
              <v-spacer></v-spacer>
              <v-btn icon class="ma-2" @click="$refs.calendar.next()">
                <v-icon>mdi-chevron-right</v-icon>
              </v-btn>
            </v-sheet>
            <v-sheet height="600">
              <v-calendar
                color="#ff9dbe"
                :weekday-format="dayToCzech"
                :month-format="weekToCzech"
                ref="calendar"
                v-model="value"
                :weekdays="weekday"
                :type="type"
                :events="events"
                :event-overlap-mode="mode"
                :event-overlap-threshold="30"
                :event-color="getEventColor"
                @change="getEvents"
                @click:event="showEvent"
                @click:more="viewDay"
                @click:date="viewDay"
                locale
               
              ></v-calendar>

              <v-menu
                v-model="selectedOpen"
                :close-on-content-click="false"
                :activator="selectedElement"
                offset-x
              >
                <v-card color="grey lighten-4" min-width="350px" flat>
                  <v-toolbar :color="selectedEvent.color" dark>
                    <!-- <v-btn icon>
                <v-icon>mdi-pencil</v-icon>
                    </v-btn>-->
                    <v-toolbar-title v-html="selectedEvent.name"></v-toolbar-title>
                    <v-spacer></v-spacer>
                    <v-btn icon>
                      <v-icon>mdi-heart</v-icon>
                    </v-btn>
                    <!-- <v-btn icon>
                <v-icon>mdi-dots-vertical</v-icon>
                    </v-btn>-->
                  </v-toolbar>
                  <v-card-text>
                    <span v-html="selectedEvent.details"></span>
                  </v-card-text>
                  <v-card-actions>
                    <v-btn text color="secondary" @click="selectedOpen = false">Zpět</v-btn>
                  </v-card-actions>
                </v-card>
              </v-menu>
            </v-sheet>
          </div>
        </template>
      </v-col>
      <v-col cols="3" class="actionsHint mt-12">
        <p style="background-color: #2196f3;">Organizace školy a vyučování</p>
        <p style="background-color: #4caf50;">Školní družina</p>
        <p style="background-color: #ff9800;">Sportovní akce</p>
        <p style="background-color: #f44336;">Předmětové akce</p>
        <p style="background-color: #9c27b0;">Kulturní akce</p>
        <p style="background-color: #009688;">Žákovský parlament</p>
      </v-col>
    </v-row>
  </div>
</template>


      

<script>

export default {
  name: "ActionsContent",
  components: {},
  data() {
    return {
      //calendar
      focus: "",
      type: "month",
      types: ["month", "week", "day"],
      // types: ['měsíc', 'týden', 'den', '4dny'],
      mode: "stack",
      modes: ["stack", "column"],
      weekday: [1, 2, 3, 4, 5],//vykendy jsem dal pryc
      weekdays: [
        //specifikuje kderé dny zobrazit !!!!vikendy dat pryc i s nabidkou vyberu, ve skole vikendy nikoho nezajimaj
        // { text: "Po - Ne", value: [1, 2, 3, 4, 5, 6, 0] },
        { text: "Po - Pá", value: [1, 2, 3, 4, 5] }
      ],
      value: "",
      start: null,
      end: null,
      selectedEvent: {},
      selectedElement: null,
      selectedOpen: false,
      events: [],

      ///calendar

      // events: events,
    //   actions: actions,
      images: {
        // sample: require("@/assets/Pln_2020-01-page-001.jpg")
      }
    };
  },
  computed: {},
  methods: {
    dayToCzech(weekday) {
      if (weekday.weekday === 0) return "Neděle";
      else if (weekday.weekday === 1) return "Pondělí";
      else if (weekday.weekday === 2) return "Úterý";
      else if (weekday.weekday === 3) return "Středa";
      else if (weekday.weekday === 4) return "Čtvrtek";
      else if (weekday.weekday === 5) return "Pátek";
      else if (weekday.weekday === 6) return "Sobota";
    },
    weekToCzech(type) {
      if (type.month === 1) return "Leden";
      else if (type.month === 2) return "Únor";
      else if (type.month === 3) return "Březen";
      else if (type.month === 4) return "Duben";
      else if (type.month === 5) return "Květen";
      else if (type.month === 6) return "Červen";
      else if (type.month === 7) return "Červenec";
      else if (type.month === 8) return "Srpen";
      else if (type.month === 9) return "Září";
      else if (type.month === 10) return "Říjen";
      else if (type.month === 11) return "Listopad";
      else if (type.month === 12) return "Prosinec";
    },
    viewDay({ date }) {
      this.focus = date;
      this.type = "day";
    },
    showEvent({ nativeEvent, event }) {
      const open = () => {
        this.selectedEvent = event;
        this.selectedElement = nativeEvent.target;
        setTimeout(() => (this.selectedOpen = true), 10);
      };

      if (this.selectedOpen) {
        this.selectedOpen = false;
        setTimeout(open, 10);
      } else {
        open();
      }

      nativeEvent.stopPropagation();
    },
    getEvents({ start, end }) {
      const events = [
        {
          name: "Notes strážníka Pavla“ 2.A,B po 2. hod.",
          start: "2020-03-03",
          // end: "2020-02-03",
          color: "blue",
          details: "TU"
        },
        
        {
          name: "MAP–Společně do školy–po a st – JIH út a čt – Úšovice a VH vždy  16.00 – 17.30",
          start: "2020-03-03",
          end: "2020-03-19",
          color: "blue",
          details: "Ger, Koz, Kle, Kar, Vit"
        },
        {
          name: "Notes strážníka Pavla“ 2.C 2 hod.",
          start: "2020-03-04",
          color: "blue",
          details: "TU"
        },
        {
          name: "Drogová prevence pro 2.st. 65,- Kč D. Nekolný 8.00  - 8. – 9. tř., 10.00 6. – 7. tř.",
          start: "2020-03-04 08:00",
          color: "blue",
          details: "Nej"
        },
        {
          name: "Jaký jsi čtenář? – místní kolo akce ŠD",
          start: "2020-03-05",
          color: "blue",
          details: "Maš."
        },
        {
          name: "Žákovský parlament",
          start: "2020-03-05",
          color: "blue",
          details: ""
        },
        {
          name: "Angličtina nás baví–školní kolo 4.–5.tř.(při Aj)",
          start: "2020-03-06",
          color: "blue",
          details: "Je, Le, Pro, Vit"
        },
        {
          name: "Dopravní výchova – 4.třídy",
          start: "2020-03-09",
          color: "blue",
          details: "Kantor"
        },
        {
          name: "MO 5.tříd 9.00 – jídelna",
          start: "2020-03-10",
          color: "blue",
          details: "Maty"
        },
        {
          name: "Basketbal 8 + 9 H + D okrsek",
          start: "2020-03-10",
          color: "blue",
          details: "Vo"
        },
        {
          name: "Návštěva městské knihovny akce ŠD",
          start: "2020-03-10 10:00",
          color: "blue",
          details: "Maš, Prů"
        },
        {
          name: "Miniházená – Lázně Kynžvart",
          start: "2020-03-11",
          color: "blue",
          details: "Hej."
        },
        {
          name: "Nekoktám, čtu“ soutěž v knihovně  po 3 ž. 4. tř.",
          start: "2020-03-12 08:30",
          // end: "2020-02-12 12:00",
          color: "blue",
          details: ""
        },
        {
          name: "Florbal 1. st. okrsek JIH",
          start: "2020-03-12",
          color: "blue",
          details: ""
        },
        {
          name: "Nejlepší hadač akce ŠD",
          start: "2020-03-12",
          color: "blue",
          details: "Maš"
        },
        {
          name: "Nekoktám, čtu“ soutěž v knihovně - po 3 ž.5.tř.",
          start: "2020-03-13 08:30",
          color: "blue",
          details: ""
        },
        {
          name: "Nejlepší skokan přes švihadlo – akce ŠD",
          start: "2020-03-13",
          color: "blue",
          details: "Kuc"
        },
        {
          name: "Stodůlecký pohár – KP   Praha",
          start: "2020-03-14",
          color: "blue",
          details: "Vod."
        },
        {
          name: "Stodůlecký pohár“ – ZPMG Praha",
          start: "2020-03-15",
          color: "blue",
          details: "Vod."
        },
        {
          name: "Návštěva knihovny 3.C",
          start: "2020-03-17",
          color: "blue",
          details: "Koz"
        },
        {
          name: "VV AŠSK",
          start: "2020-03-17",
          color: "blue",
          details: "Vo."
        },
        {
          name: "Turnaj v „Člověče, zasměj se“ akce ŠD",
          start: "2020-03-17",
          color: "blue",
          details: "Maš."
        },
        {
          name: "Dějepisná olympiáda – krajské kolo  ",
          start: "2020-03-18",
          color: "blue",
          details: "Kuč"
        },
        {
          name: "Florbal 1.st.FL okres",
          start: "2020-03-18",
          color: "blue",
          details: ""
        },
        {
          name: "Basketbal 8 + 9  okres Aš",
          start: "2020-03-18",
          color: "blue",
          details: ""
        },
        {
          name: "Čtenářská soutěž mezi družinami Úšovice a Jih akce ŠD",
          start: "2020-03-18",
          color: "blue",
          details: "Maš"
        },
        {
          name: "Angličtina nás baví“ – okres 1.stupeň    Úš",
          start: "2020-03-19 09:30",
          color: "blue",
          details: "Je"
        },
        {
          name: "Žákovský parlament",
          start: "2020-03-19 13:00",
          color: "blue",
          details: ""
        },
        {
          name: "Kde jsou v Úšovicích lékárny? Akce ŠD",
          start: "2020-03-19",
          color: "blue",
          details: "Maš, Kuc, Prů"
        },
        {
          name: "Matematický klokan  2. – 9. tř.  2.st. vybraní žáci",
          start: "2020-03-20",
          color: "blue",
          details: ""
        },
        {
          name: "OPEN krajský přebor KP – Mariánské Lázně",
          start: "2020-03-21",
          color: "blue",
          details: "Vod"
        },
        {
          name: "Memoriál Milady Duckeové + „Pohár města Mariánské Lázně“ – ZPMG – Mariánské Lázně",
          start: "2020-03-22",
          color: "blue",
          details: "Vod"
        },
        {
          name: "Návštěva knihovny 2.C",
          start: "2020-03-23",
          color: "blue",
          details: "Mat"
        },
        
        {
          name: "„Hod na cíl“ akce ŠD",
          start: "2020-03-23",
          // end: "2020-02-28",
          color: "blue",
          details:
            "Prů"
        }
        ,
        {
          name: "Pythagoriada – okresní kolo",
          start: "2020-03-23",
          end: "2020-03-26",
          color: "blue",
          details: "Mat"
        },
        {
          name: "Sudoku  mezi školami – finále 2. a  3. tříd ŠJ",
          start: "2020-03-25 09:00",
          color: "blue",
          details: "Kuč"
        },
        {
          name: "Školní dílny -  MŠ Vora",
          start: "2020-03-25 10:00",
          end: "2020-03-26 12:30",
          color: "blue",
          details: "Mat"
        },
        {
          name: "Florbal 1. st. kraj KV",
          start: "2020-03-26",
          color: "blue",
          details: ""
        },
        {
          name: "„Angličtina nás baví“ – kraj 1.stupeň",
          start: "2020-03-26",
          color: "blue",
          details: ""
        },
        {
          name: "Návrh obalu na žvýkačky akce ŠD",
          start: "2020-03-26",
          color: "blue",
          details: "Maš"
        },
        {
          name: "DVPP Malé motivační projekty",
          start: "2020-03-27",
          color: "blue",
          details: "Maš, Kuc"
        },
        {
          name: "Lidice 21 – výsledky 1. kola ",
          start: "2020-03-27",
          color: "blue",
          details: ""
        },
        {
          name: "Noc s Andersenem – přespání v knihovně 21 žáků 4. tříd ",
          start: "2020-03-27",
          ebd: "2020-03-28",
          color: "blue",
          details: "TU"
        },
        {
          name: "Dopravní výchova – 4. třídy",
          start: "2020-03-30",
          color: "blue",
          details: "Kantor"
        },
        {
          name: "Klokaní skok   -    akce ŠD",
          start: "2020-03-30",
          color: "blue",
          details: "Prů"
        },
        {
          name: "Basketbal 8 + 9  kraj KV",
          start: "2020-03-31",
          color: "blue",
          details: ""
        },
        {
          name: "„Roztančené divadlo“  8. – 9. třídy 40,- Kč",
          start: "2020-03-31 10:30",
          color: "blue",
          details: ""
        },
        
      ];

      const min = new Date(`${start.date}T00:00:00`);
      const max = new Date(`${end.date}T23:59:59`);
      const days = (max.getTime() - min.getTime()) / 86400000; //deklarace dne
      // const eventCount = this.rnd(days, days + 20);

      // for (let i = 0; i < eventCount; i++) {
      //   const allDay = this.rnd(0, 3) === 0;
      //   const firstTimestamp = this.rnd(min.getTime(), max.getTime());
      //   const first = new Date(firstTimestamp - (firstTimestamp % 900000));
      //   const secondTimestamp = this.rnd(2, allDay ? 288 : 8) * 900000;
      //   const second = new Date(first.getTime() + secondTimestamp);

      //   events.push({
      //     name: this.names[this.rnd(0, this.names.length - 1)],
      //     start: this.formatDate(first, !allDay),
      //     end: this.formatDate(second, !allDay),
      //     color: this.colors[this.rnd(0, this.colors.length - 1)]
      //   });
      // }

      this.events = events;
    },
    getEventColor(event) {
      //vraci barvu udalosti z vlastnosti color v objektu
      return event.color;
    }
    // rnd(a, b) {
    //   return Math.floor((b - a + 1) * Math.random()) + a;
    // },
    // formatDate(a, withTime) {
    //   return withTime
    //     ? `${a.getFullYear()}-${a.getMonth() +
    //         1}-${a.getDate()} ${a.getHours()}:${a.getMinutes()}`
    //     : `${a.getFullYear()}-${a.getMonth() + 1}-${a.getDate()}`;
    // }
    ///calendar
  }
};
</script>

<style scoped>
.actionsContent {
  /* margin-top: 50px; */
}
.actionsHint p {
  color: white;
  border-radius: 5px;
  text-align: left;
  text-indent: 50px;
}
</style>
