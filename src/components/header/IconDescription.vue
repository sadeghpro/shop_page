<template>
  <div class="inline-block">
    <div class="inline-block">
      <slot/>
    </div>
    <div class="inline-block font">
      <b class="title">
        {{ title }}
      </b>
      {{ description }}
    </div>
  </div>
</template>

<script>
export default {
  name: "IconDescription",
  props: {
    title: String,
    description: String,
  }
}
</script>

<style scoped>
* {
  color: #e62f35;
}
.title {
  display: block;
}
.font {
  font-size: 12px;
}
</style>
