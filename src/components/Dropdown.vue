<template>
  <div class="inline-block dropdown-main">
    <div v-on:click="showDropDown" class="dropdown-text">
      &#10069; {{ text }} &#8964;
    </div>
    <div v-if="show" class="dropdown">
      <slot />
    </div>
  </div>
</template>

<script>
export default {
  name: "Dropdown",
  data() {
    return {
      show: false
    }
  },
  props: {
    text: String,
  },
  methods: {
    showDropDown() {
      // TODO when click out side of dropdown must close it
      this.show = !this.show
    }
  }
}
</script>

<style scoped lang="scss">
.dropdown {
  position: absolute;
  z-index: 10;
  color: black;
  background-color: white;
  border: 1px solid #aaa;
}
.dropdown-text:hover {
  color: #e62f35;
}
</style>
