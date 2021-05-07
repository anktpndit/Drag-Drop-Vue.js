<template lang="en">
    <div class="body-list">
        <div class="body-list-title">
            <h2>{{title}}</h2>
        </div>
        <!-- Using slot method to pass down our orders to BodyItemItems component -->
        <slot></slot>
    </div>
</template>

<script>
export default {

  name: "BodyItemList",

  props: {
    title: {
      type: String,
    },
  },
};
</script>

<style scoped lang="scss">
.body-list-title {
  margin-bottom: 10px;
}
</style>