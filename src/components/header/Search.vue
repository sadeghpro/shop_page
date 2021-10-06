<template>
  <div class="search-main">
    <img src="@/assets/logo.png" alt="logo"/>
    <svg class="shop" width="16" height="16" fill="currentColor" viewBox="0 0 16 16">
      <path d="M0 1.5A.5.5 0 0 1 .5 1H2a.5.5 0 0 1 .485.379L2.89 3H14.5a.5.5 0 0 1 .491.592l-1.5 8A.5.5 0 0 1 13 12H4a.5.5 0 0 1-.491-.408L2.01 3.607 1.61 2H.5a.5.5 0 0 1-.5-.5zM3.102 4l1.313 7h8.17l1.313-7H3.102zM5 12a2 2 0 1 0 0 4 2 2 0 0 0 0-4zm7 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4zm-7 1a1 1 0 1 1 0 2 1 1 0 0 1 0-2zm7 0a1 1 0 1 1 0 2 1 1 0 0 1 0-2z"/>
    </svg>
    <div class="float-right desc-icon">
      <IconDescription title="No minimum order value" description="easy and quick ordering">
        <img src="@/assets/1.png"/>
      </IconDescription>
      <IconDescription title="Free delivery within the EU" description="for orders more than 100 €">
        <img src="@/assets/2.png"/>
      </IconDescription>
      <IconDescription title="5-years-guarantee" description="on all Rosenberger products">
        <img src="@/assets/3.png"/>
      </IconDescription>
      <IconDescription title="Directly from the manufacturer" description="at osi.rosenberger.shop">
        <img src="@/assets/4.png"/>
      </IconDescription>
    </div>
    <div class="search">
      <input type="text" placeholder="Search ..." />
      <!-- TODO must add width of input with animation when focus -->
      <button class="btn-search">⌕</button>
    </div>
  </div>
</template>

<script>
import IconDescription from "./IconDescription";
export default {
  name: "Search",
  components: {
    IconDescription
  }
}
</script>

<style scoped lang="scss">
.shop {
  color: #e62f35;
}
.desc-icon {
  img {
    height: 40px;
    width: 40px;
    margin-right: 10px;
    display: inline-block;
  }
}
.search-main {
  padding: 20px 50px;
  .search {
    input {
      margin: 10px 0;
      border: 1px solid #dadae5;
      color: #8798a9;
      width: 200px;
      padding: 10px;
    }
    input:focus {
      border: 1px solid black;
      color: black;
    }
    .btn-search {
      background-color: #0e233c;
      color: white;
      border: 1px solid #0e233c;
      padding: 7.5px;
    }
  }
}

</style>
