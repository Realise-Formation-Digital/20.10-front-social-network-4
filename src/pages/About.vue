<template>
  <v-content>
    <div class="staticHero">
      <v-img src="../assets/images/pexels-photo-3184360.jpeg" height="300px">
        <v-row align="end" class="lightbox white--text pa-2 fill-height">
          <v-col>
            <v-container>
              <div class="headline">About Us</div>
            </v-container>
          </v-col>
        </v-row>
      </v-img>
    </div>
    <div class="block">
      <v-container>
        <p>
          Ea pri vitae antiopam theophrastus, ut sit erat putent eruditi. Qui at
          mutat adversarium. Postulant delicatissimi ei qui, an nonumy dolorem
          nam. Cu philosophia instructior pri, nec cu mutat homero saperet, cu
          paulo ridens legendos has. Cu veri oportere pri, ad integre numquam
          iudicabit mel. Nec ea ferri iudicabit dissentiet. Ex solet melius
          omittantur his, in gloriatur vulputate mel. Ad nostro repudiandae ius,
          est amet molestie te. No est modus sensibus volutpat, et putent
          dissentias has, et sea eirmod vivendum. Paulo lucilius expetenda sea
          in, cu nam mazim sanctus ponderum. Te nam mundi corpora, dicat dolore
          debitis ius in. Indoctum adversarium definitionem an pro, an eam vidit
          utinam detracto.
        </p>
      </v-container>
    </div>

    <!-- Grid of users from API-->
    <div class="block">
      <v-container>
        <h2 class="text-center">Our Team</h2>
        <v-row>
          <v-col
            v-for="item in table"
            :key="item.id"
            class="d-flex child-flex"
            cols="12"
            sm="4"
          >
            <v-card flat tile class="mx-auto">
              <v-img
                :src="item.avatar"
                aspect-ratio="1"
                class="grey lighten-2"
              ></v-img>
              <v-card-text class="text--primary text-center">
                <div class="title">{{ item.name }}</div>
                <p>
                  {{ item.job }} <br />
                  {{ item.email }}
                </p>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </div>
  </v-content>
</template>

<script>
export default {
  name: "About",
  data() {
    return {
      table: [],
    };
  },

  async mounted() {
    try {
      //Connect to API
      const axios = require("axios");
      //Wait the response and pass the url
      const result = await axios.get("http://localhost:8000/api/users");

      //Pass result from API into table
      this.table = result.data;
    } catch (e) {
      console.log(e);
    }
  },
};
</script>
