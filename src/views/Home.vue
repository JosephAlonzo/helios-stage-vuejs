<template>
  <div>
    <h1>My user list</h1>
    <v-row class="my-2" v-for="item in users" :key="item.id.value">
      <v-col cols="12">
        <v-card class="mx-auto" elevation="4">
          <v-card-text>
            <v-list-item class="grow">
              <v-list-item-avatar color="grey darken-3">
                <v-img
                  class="elevation-6"
                  alt=""
                  :src="item.picture.thumbnail"
                ></v-img>
              </v-list-item-avatar>
              <v-list-item-content>
                <h2>
                  {{ item.name.title }} {{ item.name.last }} {{ item.name.first }}
                </h2>
                <v-divider class="mb-4"></v-divider>
                <p class="mb-1">Email: {{ item.email }}</p>
                <p>Phone Number: {{ item.cell }}</p>
              </v-list-item-content>
            </v-list-item>
          </v-card-text>
          <v-card-actions>
            <Modal :item=item class="mx-auto pb-4"></Modal>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </div>
  
</template>

<script>
import axios from "axios";
import Modal from './Modal.vue'

export default {
  data() {
    return {
      users: [],
    };
  },
  components:{
    Modal
  },
  methods: {
    getList() {
      axios.get("https://randomuser.me/api/?results=20").then((response) => {
        this.users.push(...response.data.results);
      });
    },
    scroll() {
      window.onscroll = () => {
        let bottomOfWindow = Math.floor( Math.max( window.pageYOffset,document.documentElement.scrollTop,document.body.scrollTop) + window.innerHeight) === Math.floor(document.documentElement.offsetHeight);
        if (bottomOfWindow) {
          this.getList();
        }
      };
    },
  },
  created() {
    this.getList();
    this.scroll();
  },
};
</script>
