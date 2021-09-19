<template>
<div class="v-carousel-item">
  <div class="name">
    {{item_data.name}}
  </div>
</div>
</template>

<script>
export default {
  name: "v-carousel-item",
  props: {
    item_data: {
      type: Object,
      default: () => {}
    }
  }
}
</script>

<style scoped>
.v-carousel-item{
  box-sizing: border-box;
  min-width: 300px;
  padding: 50px 0;
  border: 1px solid black;
}
.v-carousel-item .name{
  text-transform: uppercase;
  font-weight: bold;
}
</style>