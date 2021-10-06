<template>
  <div>
    <Contact v-bind:data="contact"/>
    <Search />
    <Menu />
  </div>
</template>

<script>
import Contact from './Contact';
import Search from "./Search";
import Menu from "./Menu";

export default {
  name: "Header",
  components: {
    Contact,
    Search,
    Menu,
  },
  props: {
    contact: Object
  }
}
</script>

<style scoped lang="scss">

</style>
