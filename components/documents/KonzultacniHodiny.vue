<template>
  <div>
    <template>
      <v-simple-table>
        <template v-slot:default>
          <thead>
            <tr>
              <th class="text-left">Jméno</th>
              <th class="text-left">Konzultační čas</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item in teachers" :key="item.name">
              <td>{{ item.name }}</td>
              <td>{{ item.hour }}</td>
            </tr>
          </tbody>
        </template>
      </v-simple-table>
    </template>
  </div>
</template>


<script>
export default {
  name: "KonzultacniHodiny",
  components: {},
  data() {
    return {
      teachers: [
        {
          name: "Sahánková",
          hour: "úterý 14:00 – 15:00, středa 11:40 – 12:35"
        },
        {
          name: "Wenzlová",
          hour: "úterý 11:50 – 12:35"
        },
        {
          name: "Nápravníková",
          hour: "úterý 07:10 – 08:00"
        },
        {
          name: "Pecherová",
          hour: "úterý 07:10 – 08:00"
        },
        {
          name: "Matějková",
          hour: "pátek 12:00 -13:00"
        },
        {
          name: "Ležatková",
          hour: "úterý 12:50 – 13:30"
        },
        {
          name: "Gersdorfová",
          hour: "středa 13:00 – 13:45"
        },
        {
          name: "Kozicová Kávová",
          hour: "středa 13:00 – 13:45"
        },
        {
          name: "Donut",
          hour: 452
        },
        {
          name: "KitKat",
          hour: 518
        },
        { name: "Schneiderwinklová", hour: "úterý 07:00 – 07:30" },
        { name: "Balvínová", hour: "pondělí  07:10 – 07:55" },
        { name: "Růžičková", hour: "pátek  07:15 – 08:00" },
        {
          name: "Klečková",
          hour: "denně  07:15 – 07:40, jako vých. poradce 13:00 – 14:00"
        },
        { name: "Vithová", hour: "čtvrtek 07:15 – 07:40" },
        { name: "Karenovičová", hour: "denně  06:30 – 07:40" },
        {
          name: "Mikysková",
          hour: "pondělí 10:50 – 11:40, středa 11:50 – 12:30"
        },
        {
          name: "Krystyníková",
          hour: "úterý 13:00 -  14:00, čtvrtek 07:10 – 07:55"
        },
        { name: "Matysová", hour: "středa – pátek 07:15 – 07:50" },
        { name: "Milfaitová", hour: "pondělí 10:55 – 11:40" },
        { name: "Špiříková", hour: "pondělí  14:00 – 15:00" },
        { name: "Kreuzová", hour: "pátek 11:50 – 12:40" },
        { name: "Jelínková", hour: "čtvrtek 10:00 – 11:00" },
        { name: "Zeithamel", hour: "čtvrtek 08:55 – 09:40" },
        { name: "Fišáková", hour: "pondělí 08:00 – 10:00" },
        { name: "Záhorová", hour: "pátek 08:55 – 09:40" },
        { name: "Čížková", hour: "úterý 07:15 – 07:45" },
        { name: "Vodičková", hour: "čtvrtek  08: 00 – 08:30" },
        { name: "Habal", hour: "úterý 07:40 – 08:00" },
        { name: "Hrubá", hour: "středa 07:30 – 08:00, 14:00 – 14:30" },
        { name: "Jauris", hour: "čtvrtek 13:30 – 14:00" },
        { name: "Ledererová", hour: "středa 12:30 -13:30" },
        { name: "Staňková", hour: "středa 11:40 – 12:30" },
        { name: "Šebeková", hour: "pátek 10:55 – 11:40" },
        { name: "Vojnovič", hour: "středa 13:00 – 14:00" },
        { name: "Preňková", hour: "úterý 12:30 – 13:30" },
        { name: "Kučavová", hour: "pondělí – středa 07:00 – 07:40" }
      ]
    };
  }
};
</script>