
<template>
  <div class="stock">
    <div class="stock-item" v-for="value in stock" :key="value.stock">
      <div class="stock-item__info">
        <div class="stock-item__cover">
          <img :src="value.image" :alt="value.companyName">
        </div>
        <h3 class="stock-item__title">
          {{ value.companyName }}
          <span>{{ value.symbol }}</span>
        </h3>
      </div>
      <span class="stock-item__price">{{ value.price }} </span>
    </div>
  </div>
  <h3>Get Info</h3>
  <select v-model="selected">
    <option value="" disabled>Select Company</option>
    <option v-for="value in stock" :key="value.stock" :value="value.description">{{ value.companyName }}</option>
  </select>
  <div class="div info">
    {{ selected }}
  </div>
  </template>

<script lang="ts">
  import axois from 'axios'
import axios from 'axios'

  export default {
    name: 'Stocks',
    data() {
      return {
        stock: [],
        errors: [],
        selected: ''
      }
    },
    created() {
     axios.get('https://financialmodelingprep.com/api/v3/profile/OZON?apikey=f1d8acd9e64a53e91bcb16168cc1efe4')
     .then(responce => {
       this.stock = responce.data
       console.log(responce)
     })
     .catch(e => {
       this.errors.push(e)
     })
  }
}
</script>

