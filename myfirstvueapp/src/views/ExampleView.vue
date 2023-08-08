<script setup>
import { ref } from 'vue'

const itemId = ref(0)
const shoppingitem = ref('')
const shoppinglist = ref([])
const shopped = ref(false)

function addItem() {
    shoppinglist.value.push({
        id: itemId.value++,
        item: shoppingitem.value,
        status: shopped.value
    })
    shoppingitem.value = ""
}

function removeItem(i) {
    shoppinglist.value = shoppinglist.value.filter((t) => t !== i)
}

// Composition API with SFC .vue
</script>

<template>
<div>
    <h1>My Shopping List</h1>
    <input type="text" v-model="shoppingitem">
    <button @click="addItem">Add Item</button>
    <ol>
        
        <li v-for="i in shoppinglist">
        <input type="checkbox" v-model="i.shopped">

        <span :class="{done: i.shopped}"> {{ i.item }}</span>
       
      
        <button  @click="removeItem(i)">X</button>
        </li>
    </ol>
</div>
</template>

<style scoped>

.divstyle {
  width: 100%;
  height: 400px;
  background-color: aquamarine;
  padding: 70px;
}
.done {
    text-decoration: line-through;
}
input[type="text"] {
width: 80%;
padding: 10px;
font-size: 20px;
align-content: center;
}

input[type="checkbox"] {
font-size: 20px;
margin-right: 1px;
}

.buttonstyle {
width: 80%;
background-color: #4caf50;
color: white;
padding: 14px 20px;
margin: 8px 0;
border: none;
border-radius: 4px;
cursor: pointer;
}

div {
border-radius: 5px;
background-color: #f2f2f2;
padding: 20px;
}
h1 {
width: 100%;
text-align: center;
}

span {
padding: 20px;
font-size: 20px;
}
li {
width: 100%;
}

</style>