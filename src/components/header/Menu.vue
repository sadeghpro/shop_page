<template>
  <div>
    <div class="placeholder" v-bind:class="scrolled? 'show' : ''"></div>
    <div v-on="handleScroll" class="menu" v-bind:class="scrolled? 'sticky' : ''">
      <div class="float-right icons">
        <div class="icon">
          <svg class="shop" width="18" height="18" fill="currentColor" viewBox="0 0 16 16">
            <path
                d="M0 1.5A.5.5 0 0 1 .5 1H2a.5.5 0 0 1 .485.379L2.89 3H14.5a.5.5 0 0 1 .491.592l-1.5 8A.5.5 0 0 1 13 12H4a.5.5 0 0 1-.491-.408L2.01 3.607 1.61 2H.5a.5.5 0 0 1-.5-.5zM3.102 4l1.313 7h8.17l1.313-7H3.102zM5 12a2 2 0 1 0 0 4 2 2 0 0 0 0-4zm7 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4zm-7 1a1 1 0 1 1 0 2 1 1 0 0 1 0-2zm7 0a1 1 0 1 1 0 2 1 1 0 0 1 0-2z"/>
          </svg>
        </div>
        <div class="icon">
          <svg width="18" height="18" fill="currentColor" viewBox="0 0 16 16">
            <path d="M3 14s-1 0-1-1 1-4 6-4 6 3 6 4-1 1-1 1H3zm5-6a3 3 0 1 0 0-6 3 3 0 0 0 0 6z"/>
          </svg>
        </div>
        <div class="icon">
          <svg width="18" height="18" fill="currentColor" viewBox="0 0 16 16">
            <path
                d="M14.5 3a.5.5 0 0 1 .5.5v9a.5.5 0 0 1-.5.5h-13a.5.5 0 0 1-.5-.5v-9a.5.5 0 0 1 .5-.5h13zm-13-1A1.5 1.5 0 0 0 0 3.5v9A1.5 1.5 0 0 0 1.5 14h13a1.5 1.5 0 0 0 1.5-1.5v-9A1.5 1.5 0 0 0 14.5 2h-13z"/>
            <path
                d="M3 5.5a.5.5 0 0 1 .5-.5h9a.5.5 0 0 1 0 1h-9a.5.5 0 0 1-.5-.5zM3 8a.5.5 0 0 1 .5-.5h9a.5.5 0 0 1 0 1h-9A.5.5 0 0 1 3 8zm0 2.5a.5.5 0 0 1 .5-.5h6a.5.5 0 0 1 0 1h-6a.5.5 0 0 1-.5-.5z"/>
          </svg>
        </div>
      </div>
      <ul>
        <!-- TODO add sub menu -->
        <li>FO trunks</li>
        <li class="active">FO patchcords</li>
        <li>FO cable & panel</li>
        <li>Copper cabling</li>
        <li>New in our shop</li>
        <li>Shop offers</li>
        <li>About us</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "Menu",
  data() {
    return {
      limitPosition: 169, //TODO must calculate dynamically
      scrolled: false,
      lastPosition: 0
    };
  },
  methods: {
    handleScroll() {
      if (this.lastPosition < window.scrollY && this.limitPosition < window.scrollY) {
        this.scrolled = true;
      }

      if (this.lastPosition > window.scrollY && this.limitPosition > window.scrollY) {
        this.scrolled = false;
      }

      this.lastPosition = window.scrollY;
    }
  },
  created() {
    window.addEventListener("scroll", this.handleScroll);
  },
  destroyed() {
    window.removeEventListener("scroll", this.handleScroll);
  }
}
</script>

<style scoped lang="scss">
.icons {
  padding: 3px;

  .icon {
    border-radius: 50%;
    padding: 5px;
    border: 2px solid #0e233c;
    color: #0e233c;
    margin: 2px 10px;
    display: inline-block;
    width: 18px;
    height: 18px;
  }

  .icon:hover {
    background-color: #0e233c;
    color: white;
  }
}

.menu {
  border: 1px solid #d4d7de
}

ul {
  margin: 0
}

li {
  display: inline-block;
  list-style: none;
  margin: 0 10px;
  padding: 10px;
}

li:hover {
  color: #e62f35;
}

.active {
  border-top: 3px solid #e62f35;
  color: #e62f35
}

.sticky {
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  z-index: 2999;
  width: 100%;
  box-shadow: 0 1px 10px rgba(0, 0, 0, 0.2);
  background: white;
}
.placeholder {
  width: 100%;
  height: 0;
}
.placeholder.show {
  width: 100%;
  height: 44.5px;
}
</style>
