<template>

    <!-- Making cards to display our orders -->
    <div class="body-item-div">
        <v-card class="mx-auto body-item-card" elevation="20" color="transparent" max-width="200">
            <v-list-item three-line>
                <v-list-item-content>
                    <div class="overline mb-1">
                        {{ item.orderDate.slice(0, 10) }}
                    </div>
                    <v-list-item-title class="mb-4">
                        {{ item.orderName }}
                    </v-list-item-title>
                </v-list-item-content>
            </v-list-item>
        </v-card>
    </div>
</template>

<script>
export default {

  name: "BodyItemItems",
  
  props: {
    item: {
      type: Object,
    },
  },
};
</script>

<style scoped lang="scss">
.body-item-card {
    padding: 10px;
}
.body-item-card:hover {
  cursor: move;
}
</style>