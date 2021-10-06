<template>
  <div class="breadcrumb">
    <div class="overview"><span class="arrow">&lsaquo;</span> Overview</div>
    <ul class="inline-block list">
      <li v-bind:key="category" v-for="category in categories">
        {{ category }} <span class="arrow">&rsaquo;</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Breadcrumb",
  props: {
    categories: Array
  }
}
</script>

<style scoped lang="scss">
.list li:last-child {
  color: #e62f35;
  span.arrow {
    display: none;
  }
}
.breadcrumb {
  margin: 0 60px;
}
li {
  display: inline-block;
  list-style: none;
  margin: 0 10px;
  font-size: 14px;
  font-weight: 300;

}
.overview {
  display: inline-block;
  margin: 0 25px;
  font-size: 14px;
  font-weight: 300;
}
.overview:hover, li:hover {
  color: #e62f35;
}
.arrow {
  font-size: 20px;
}
</style>
