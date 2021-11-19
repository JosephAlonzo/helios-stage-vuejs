<template>
  <div>
    <v-row justify="center">
      <v-dialog v-model="dialog" persistent max-width="374px">
        <template v-slot:activator="{ on, attrs }">
          <v-btn color="primary" dark v-bind="attrs" v-on="on">
            Plus d'informations
          </v-btn>
        </template>
        <v-card width="374px">
          <template slot="progress">
            <v-progress-linear
              color="deep-purple"
              height="10"
              indeterminate
            ></v-progress-linear>
          </template>

          <v-img
            height="200"
            :src="item.picture.large"
          ></v-img>

          <v-card-title>{{ item.name.title }} {{ item.name.last }} {{ item.name.first }}</v-card-title>
          
          <v-card-text class="mt-0">
            <div class="mb-0 text-subtitle-1">{{item.gender}}</div>
          </v-card-text>

          <v-divider class="mx-2"></v-divider>

          <v-card-title>Mes informations</v-card-title>

          <v-card-text>
            <div>
              Adresse: <br>{{item.location.street.number}} {{item.location.street.name}} {{item.location.city}} {{item.location.state}} {{item.location.postcode}}
              <br>Email: <br> {{item.email}}
              <br>Téléphone: <br> {{item.phone}}
            </div>
          </v-card-text>

          <v-card-actions>
            <v-btn color="deep-purple lighten-2" text @click="dialog = false" class="mb-2">
              Fermer
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-row>
  </div>
</template>

<script>
//text @click="dialog = false">
export default {
  name: "Modal",
  props: ["item"],
  data() {
    return {
      dialog: false,
    };
  },
  created() {
  },
};
</script>
