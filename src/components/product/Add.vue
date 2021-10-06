<template>
  <div>
    <!-- TODO add image zoom library -->
    <img v-bind:alt="product.name" v-bind:src="product.image">
    <div class="form">
      <div class="price"><span v-if="selected === null">From</span> €{{ (product.price + ((length - 1) * product.pricePerSize)).toFixed(2) }}</div> (excl. VAT)
      <div><span v-if="selected === null">From</span> €{{ (((product.price + ((length - 1) * product.pricePerSize)) * product.tax / 100) + product.price).toFixed(2) }} (incl. {{ product.tax }}% VAT) </div>
      <br/>
      <div>
        <b>Length in stock</b>
        <div class="button-group">
          <button v-on:click="select" v-bind:class="selected == 0 ? 'selected' : ''" data-key="0">Custom Length</button>
          <button v-on:click="select" v-bind:class="selected == 1 ? 'selected' : ''" data-key="1">1</button>
          <button v-on:click="select" v-bind:class="selected == 2 ? 'selected' : ''" data-key="2">2</button>
          <button v-on:click="select" v-bind:class="selected == 3 ? 'selected' : ''" data-key="3">3</button>
          <button v-on:click="select" v-bind:class="selected == 5 ? 'selected' : ''" data-key="5">5</button>
          <button v-on:click="select" v-bind:class="selected == 10 ? 'selected' : ''" data-key="10">10</button>
        </div>
        <br/>
        <div  v-if="selected !== null">
          <button v-on:click="reset" class="reset">&#x2715; Reset selection</button>
          <br/>
          <br/>
        </div>
        <div v-if="selected === null || selected === '0'">
          <div>Länge :</div>
          <input v-on:change="validationCustomLength" v-on:keyup="validationCustomLength" value="1" class="length" type="number" min="1" max="50" step=".5" /> m
          <div v-bind:class="error ? 'error' : 'success'">You can order from 1 m to 50 m in 0,5 m steps.</div>
        </div>
        <br/>
        <div>
          <select v-on:change="changeCount" class="select-count">
            <option v-for="count in 200" v-bind:key="count" v-bind:value="count">{{ count }}</option>
          </select>
          <button v-on:click="add" class="btn-add">Add to shopping cart</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Add",
  data() {
    return {
      selected: null,
      error: false,
      length: 1,
      count: 1,
    }
  },
  props: {
    product: Object,
  },
  methods: {
    select(event) {
      this.selected = event.target.getAttribute("data-key")
      this.length = event.target.getAttribute("data-key") === 0 ? 1 : event.target.getAttribute("data-key")
    },
    validationCustomLength(event) {
      this.error = Number(event.target.value) % 0.5 !== 0 || Number(event.target.value) > 50 || Number(event.target.value) < 1;
      if (!this.error) {
        this.length = Number(event.target.value)
      }
    },
    reset() {
      this.selected = null;
      this.length = 0;
      this.error = false;
    },
    add() {
      console.log({
        productId: this.product.id,
        length: Number(this.length),
        count: this.count,
      })
    },
    changeCount(event) {
      console.log(event.target.value)
      this.count = Number(event.target.value);
    }
  }
}
</script>

<style scoped lang="scss">
.form {
  width: 40%;
  float: right;
  .price {
    font-weight: 700;
    font-size: 28px;
    display: inline-block;
  }
  .button-group {
    display: block;
    button {
      width: 27%;
      height: 50px;
      background-color: white;
      color: black;
      border: 1px solid #ececf2;
      margin: 2px;
      overflow: hidden;
      word-wrap: break-word;
      text-overflow: ellipsis;
    }
    button:hover {
      color: #e62f35;
      border: 1px solid #e62f35;
    }
    .selected {
      color: #e62f35;
      border: 1px solid #e62f35;
    }
  }
  .length {
    margin: 10px 0;
    border: 1px solid #dadae5;
    color: #8798a9;
    width: 60px;
    padding: 10px;
  }
  .length:focus {
    border: 1px solid black;
    color: black;
  }
  .error {
    color: #e62f35;
  }
  .success {
    color: #2ecc71;
  }
  .reset {
    background-image: linear-gradient(to bottom, #fff 0%, #f8f8fa 100%);
    border: 1px solid #dadae5;
    color: #0e233c;
    font-size: 0.875rem;
    font-weight: 600;
    line-height: 2rem;
  }
  .reset:hover {
    background: #666 !important;
    color: #fff;
  }
  .select-count {
    font-size: 1rem;
    font-weight: 700;
  }
  .btn-add {
    margin-left: 10px;
    position: relative;
    background: #0e233c;
    color: white;
    border: 1px solid #0e233c;
    padding: 10px 25px;
    font-size: 1rem;
  }
  .btn-add:after {
    content: "›";
    position: absolute;
    right: 10px;
    width:2px;
  }
  .btn-add:hover {
    background: #e62f35;
    border: 1px solid #e62f35;
  }
}
</style>
