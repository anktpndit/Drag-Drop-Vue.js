<template lang="en">
    <v-main app style="background-color:#272727;">
      <v-container fill-height class="body-container">

        <!-- Loading if data has not been yet received. -->
        <atom-spinner 
          v-if="loading"
          :animation-duration="1000"
          :size="60"
          color="#ff1d5e"
          align="center"
          class="ma-auto"
        />

         <!-- Using if-else statement to display drag&drop feature only when we have some order -->
        <v-row class="body-container-row" v-if="(ourData['internal-need'].length) || (ourData['shopping-cart'].length)">
          <v-col xs="12" sm="12" md="6" lg="6" align="center">
              <body-item-list title="Internal Need">
                <vue-draggable :list="ourData['internal-need']" group="sameGroup" ghostClass="on-drag" animation="400">
                  <body-item-items v-for="item in idGeneratorForInternalNeed" :key="item.id" :item="item"></body-item-items>
                </vue-draggable>
              </body-item-list>
          </v-col>
          <v-col xs="12" sm="12" md="6" lg="6" align="center">
              <body-item-list title="Shopping Cart">
                <vue-draggable :list="ourData['shopping-cart']" group="sameGroup" ghostClass="on-drag" animation="400">
                  <body-item-items v-for="item in idGeneratorForShoppingCart" :key="item.id" :item="item"></body-item-items>
                </vue-draggable>
              </body-item-list>
          </v-col>
        </v-row>

        <!-- Displaying an error if there is no order -->
        <v-row v-else-if="!loading" class="my-auto">
          <v-col align="center">
            <v-alert max-width="300" type="error">
              You haven't orderd anything!
            </v-alert>
          </v-col>
        </v-row>
        
      </v-container>
    </v-main>
</template>

<script>

//importing Body Components
import BodyItemList from "./BodyItemList";
import BodyItemItems from "./BodyItemItems";

//importing npm packages
import vueDraggable from "vuedraggable";
import { AtomSpinner } from 'epic-spinners'

export default {

  name: "Body",

  components: {
    "body-item-list": BodyItemList,
    "body-item-items": BodyItemItems,
    "vue-draggable": vueDraggable,
    "atom-spinner": AtomSpinner,
  },

  data() {
    return {
      loading: true,
      ourData : {
        //order goes to one of the array below
        'internal-need' : [],
        'shopping-cart': [],
      },
    };
  },

  computed: {

    //Creating ids for our orders
    idGeneratorForInternalNeed() {
      return this.ourData['internal-need']?.map((currentValue, index) => ({
        ...currentValue,
        id: index + 1,
      }));
    },
    idGeneratorForShoppingCart() {
      return this.ourData['shopping-cart']?.map((currentValue, index) => ({
        ...currentValue,
        id: index + this.ourData['internal-need'].length,
      }));
    },
  },

  // Using mounted hook to fetch and initialize orders
  created : function () {
    fetch("orderItems.json")
      .then((response) => response.json())
      .then((data) => {
          this.ourData['internal-need'] = (data['internal-need'] ? data['internal-need'] : []);
          this.ourData['shopping-cart'] = (data['shopping-cart'] ? data['shopping-cart'] : []);
          this.loading = false;
      })
      .catch((error) => {
        console.log('Request failed', error)
      });
  },
};
</script>

<style scoped lang="scss">
.body-noorder-col{
  width: 5%;
}
.body-container {
  align-items: flex-start;
}
.body-container-row {
  margin-top: 7%;
  padding: 0 20% 0 20%;
}
.on-drag {
  background-color: aquamarine;
}
</style>