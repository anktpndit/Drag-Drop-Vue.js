
<template>

  <!-- FOOTER -->

  <v-footer app class="pt-7 the-footer">
    <v-card style="background:#272727;" class="flex mx-auto" flat tile max-width="1000">
      <v-card-title class="teal rounded-xl pa-2">
        <!-- Added v-flex to make the contents more responsive -->
        <v-flex xs12 md6>
          <div class="text-center">
            <strong class="subheading">
              Get connected with us on social networks!
            </strong>
          </div>
        </v-flex>
        <v-flex xs12 md6>
          <div class="text-center">
            <v-btn v-for="icon in icons" :key="icon" class="mx-4" dark icon>
              <v-icon size="24px">
                {{ icon }}
              </v-icon>
            </v-btn>
          </div>
        </v-flex>
      </v-card-title>

      <v-card-text class="py-2 white--text text-center">
        {{ new Date().getFullYear() }} — <strong>Veutify</strong>
      </v-card-text>
    </v-card>
  </v-footer>
</template>

<script>
export default {

  name: "Footer",
  
  data: () => ({
    icons: ["mdi-facebook", "mdi-twitter", "mdi-linkedin", "mdi-instagram"],
  }),
};
</script>

<style scoped lang="scss">
</style>