<template>
  <div>
    <Header v-bind:contact="contact"/>
    <Breadcrumb v-bind:categories="product.categories"/>
    <Product v-bind:product="product"/>
  </div>
</template>

<script>
import Header from './components/header/Header'
import Breadcrumb from './components/Breadcrumb'
import Product from './components/product/Product'
//TODO add site bottom

export default {
  name: 'App',
  components: {
    Header,
    Breadcrumb,
    Product,
  },
  data() {
    return {
      contact: {
        phoneNumber: '+49(821)24924-1000',
        email: 'webshop-osi@rosenberger.com',
        facebook: 'https://www.facebook.com/rosenberger.osi',
        twitter: 'https://twitter.com/RosenbergerOSI',
        linkedin: 'https://www.linkedin.com/company/rosenberger-osi-gmbh-&-co.-ohg/',
        youtube: 'https://www.youtube.com/playlist?list=PLUbdpuA9sqbeuQvmWDCIORvCLd_jMraY3',
      },
      product: {
        id: 2,
        categories: [
          "LWL Patchkabel",
          "Patchkabel Duplex",
          "Singlemode OS2 ",
        ],
        name: 'Fiber optic patch cord duplex singlemode OS2, SC-PC/SC-PC, I-V(ZN)H 2x 2,1 mm',
        description: 'High quality fiber optic fiber patch cord duplex with SC-PC duplex connector, polarity crossed and changeable, FRNC indoor cable zipcord figure „8“ 2x 2,1 mm, I-V(ZN)H 2x1E9/125µ yellow, G657.A1 bend insensitive. 062A1726G657A1',
        image: '/LWL-Patchkabel-SC-Duplex.jpg',
        price: 13.73,
        pricePerSize: 0.28,
        tax: 19
      }
    }
  }
}
</script>

<style lang="scss">
:root {
  --radius: 2px;
  --baseFg: dimgray;
  --baseBg: white;
  --accentFg: #000;
  --accentBg: #fff;
}

html, body {
  font-family: "Open Sans", "Helvetica Neue", Helvetica, Arial, "Lucida Grande", sans-serif;
  margin: 0;
}
.inline-block {
  display: inline-block;
}
.float-right {
  float: right;
}
textarea:focus, input:focus{
  outline: none;
}
select {
  font: 400 12px/1.3 sans-serif;
  -webkit-appearance: none;
  appearance: none;
  color: var(--baseFg);
  border: 1px solid var(--baseFg);
  line-height: 1;
  outline: 0;
  padding: 0.65em 2.5em 0.55em 0.75em;
  border-radius: var(--radius);
  background-color: var(--baseBg);
  background-image: linear-gradient(var(--baseFg), var(--baseFg)),
  linear-gradient(-135deg, transparent 50%, var(--accentBg) 50%),
  linear-gradient(-225deg, transparent 50%, var(--accentBg) 50%),
  linear-gradient(var(--accentBg) 42%, var(--accentFg) 42%);
  background-repeat: no-repeat, no-repeat, no-repeat, no-repeat;
  background-size: 1px 100%, 20px 22px, 20px 22px, 20px 100%;
  background-position: right 20px center, right bottom, right bottom, right bottom;
}

select:hover {
  background-image: linear-gradient(var(--accentFg), var(--accentFg)),
  linear-gradient(-135deg, transparent 50%, var(--accentBg) 50%),
  linear-gradient(-225deg, transparent 50%, var(--accentBg) 50%),
  linear-gradient(var(--accentBg) 42%, var(--accentFg) 42%);
}
</style>
