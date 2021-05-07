<template lang="en">

  <!-- APP BAR -->

  <div>
    <v-app-bar color="#009688" dense>
        <v-spacer />
        <v-app-bar-nav-icon class="ml-auto"></v-app-bar-nav-icon>
        <v-spacer />
        <v-toolbar-title>#coding-challenge</v-toolbar-title>
        <v-spacer/>
        <v-btn icon>
          <v-icon>mdi-heart</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>

        <v-menu left bottom>
          <template v-slot:activator="{ on, attrs }">
            <v-btn icon v-bind="attrs" v-on="on">
              <v-icon>mdi-dots-vertical</v-icon>
            </v-btn>
          </template>

          <v-list>
            <v-list-item v-for="n in 5" :key="n" @click="() => {}">
              <v-list-item-title>Option {{ n }}</v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
        <v-spacer />
    </v-app-bar>
  </div>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style scoped lang="en">
</style>