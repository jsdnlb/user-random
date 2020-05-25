<template>
  <v-container class="align-center mb-6">
    <v-card class="mx-auto mb-5" max-width="344" outlined>
      <v-list-item three-line>
        <v-list-item-content>
          <v-list-item-title class="headline mb-1"
            >Desarrollado por:
          </v-list-item-title>
          <v-list-item-subtitle>Daniel Buitrago </v-list-item-subtitle>
          <v-list-item-subtitle class=".font-italic font-weight-bold	"
            >Github: jsdnlb</v-list-item-subtitle
          >
        </v-list-item-content>

        <v-list-item-avatar tile size="80">
          <img
            src="https://avatars1.githubusercontent.com/u/17171887?s=400&u=ce41602e521530094615d316e263dd2c2598068c&v=4"
            alt="jsdnlb"
          />
        </v-list-item-avatar>
      </v-list-item>
    </v-card>
    <v-card class="mx-auto" max-width="344">
      <v-img :src="userRandom[0].picture.large" height="250px"></v-img>

      <v-card-title>
        {{ userRandom[0].name.title }} {{ userRandom[0].name.first }}
        {{ userRandom[0].name.last }}
      </v-card-title>

      <v-card-subtitle>
        <div class="d-flex flex-column mb-6">
          <v-chip class="mb-2" color="orange" text-color="white">
            <v-icon class="mr-2">fa-mobile</v-icon>
            {{ userRandom[0].phone }}
          </v-chip>
          <v-chip color="orange" text-color="white">
            <v-icon class="mr-2">fa-street-view</v-icon>
            {{ userRandom[0].location.city }} -
            {{ userRandom[0].location.state }} -
            {{ userRandom[0].location.country }}
          </v-chip>
        </div>
      </v-card-subtitle>

      <v-card-actions>
        <v-btn text>Share</v-btn>

        <v-btn color="purple" text>
          Explore
        </v-btn>

        <v-spacer></v-spacer>

        <v-btn icon @click="show = !show">
          <v-icon>{{ show ? "fa-angle-up" : "fa-angle-down" }}</v-icon>
        </v-btn>
      </v-card-actions>

      <v-expand-transition>
        <div v-show="show">
          <v-divider></v-divider>

          <v-card-text>
            I'm a thing. But, like most politicians, he promised more than he
            could deliver. You won't have time for sleeping, soldier, not with
            all the bed making you'll be doing. Then we'll go with that data
            file! Hey, you add a one and two zeros to that or we walk! You're
            going to do his laundry? I've got to find a way to escape.
          </v-card-text>
        </div>
      </v-expand-transition>
    </v-card>
  </v-container>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      nameApp: "user-random",
      show: false,
      userRandom: [
        {
          gender: "female",
          name: { title: "Miss", first: "Deniz", last: "Kavaklıoğlu" },
          location: {
            street: { number: 36, name: "Atatürk Sk" },
            city: "Rize",
            state: "Gümüşhane",
            country: "Turkey",
            postcode: 32287,
            coordinates: { latitude: "69.4123", longitude: "88.7411" },
            timezone: {
              offset: "+5:00",
              description: "Ekaterinburg, Islamabad, Karachi, Tashkent",
            },
          },
          email: "deniz.kavaklioglu@example.com",
          login: {
            uuid: "474b00a5-3be5-415d-aefa-d4f687b49afb",
            username: "redsnake339",
            password: "warning",
            salt: "S3vfx1Q3",
            md5: "e975b4abb7edb4df505c4318740601af",
            sha1: "3aea9aed5e0a1a0145e40843d278f404e4a783ef",
            sha256:
              "7f7164969986cc8918a5c2e8b49ee8c066927f1bf4398f994b01946e3e023b12",
          },
          dob: { date: "1998-02-25T09:02:45.359Z", age: 22 },
          registered: { date: "2009-07-24T04:33:40.151Z", age: 11 },
          phone: "(472)-569-7330",
          cell: "(028)-469-2709",
          id: { name: "", value: null },
          picture: {
            large: "https://randomuser.me/api/portraits/women/53.jpg",
            medium: "https://randomuser.me/api/portraits/med/women/53.jpg",
            thumbnail: "https://randomuser.me/api/portraits/thumb/women/53.jpg",
          },
          nat: "TR",
        },
      ],
    };
  },
  mounted() {
    // console.log("Hola desde mounted");
    this.getUsers();
  },
  methods: {
    getUsers() {
      // console.log("Hola desde methods");
      axios
        .get("https://randomuser.me/api/")
        .then((res) => {
          // console.log(res.data.results);
          this.userRandom = res.data.results;
        })
        .catch((e) => console.log(e));
    },
  },
};
</script>
