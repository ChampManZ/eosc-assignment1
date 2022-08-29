<script setup>
  import { reactive, ref } from 'vue'

  // Lab Area
  // const counter = reactive({ count: 0 })
  // const message = ref('Hello, World')
  // const fullnameId = ref('fullnameId')
  // const list = ref('')
  // const headerBool = ref(true)

  // function increment() {
  //   counter.count++
  // }

  // function toggleHeader() {
  //   headerBool.value = !headerBool.value
  // }

  let id = 0

  const newShopList = ref('')
  const shopList = ref([])
  const headerBool = ref(false)
  const displayTextWarn = ref('')
  
  function addShopList() {
    if (newShopList.value != "") {
      shopList.value.push({ id: id++, text: newShopList.value })
      newShopList.value = ''
      displayTextWarn.value = ''
      headerBool.value = false
    } else {
      displayTextWarn.value = 'Please enter a list!'
      headerBool.value = true
    }
    console.log(displayTextWarn.value)
    console.log(headerBool.value)
  }

  function removeShopList(sl) {
    shopList.value = shopList.value.filter((s) => s !== sl)
  }

  function removeAllList() {
    shopList.value = []
    newShopList.value = ''
  }
</script>

<template>
  <!-- Lab Area -->
  <!-- <h1 :class="fullnameId" v-if="headerBool">{{ message }}</h1>
  <h1 v-else>Thanapat Eurboonyanun</h1>
  <button @click="toggleHeader">Bello</button>
  <p>Count is: {{ counter.count }}</p>
  <button @click="counter.count++">CLICK ME!</button> <br>
  <button @click="increment">I WORK THE SAME!</button> <br>
  <input v-model="list" placeholder="eg. Egg x2">
  <p>{{ list }}</p> -->

  <header class="headerClass">
    <img src="./assets/Seal_of_King_Mongkut's_Institute_of_Technology_Ladkrabang.svg.png" alt="KMITL Logo" width="75" height="75">
    <h1>Shopping List</h1>
    <h1>by: 63011342</h1>
  </header> <br>
  <div class="formArea">
    <h3>Add an item here</h3>
    <form @submit.prevent="addShopList">
    <input v-model="newShopList" placeholder="eg. Egg x2">
    <button @keyup.enter="addShopList" class="addBtn">Add</button>
    </form>
  </div>
  <div class="listArea">
    <ul class="ulClass">
      <li v-for="i in shopList" :key="i.id">
        {{ i.text }}
        <button @click="removeShopList(i)" class="rmvBtn">X</button>
      </li>
    </ul> <br>
    <button @click="removeAllList" class="clearBtn">Clear</button>
  </div> <br>
  <h1 v-if="headerBool" class="ntfHead">{{ displayTextWarn }}</h1>
  <h1 v-else></h1>
</template>

<style scoped>

</style>
