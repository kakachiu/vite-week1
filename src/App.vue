<template>
  <table class="table table-hover">
    <thead class="table-dark">
      <tr>
        <th scope="col" width="200">品項</th>
        <th scope="col" width="300">描述</th>
        <th scope="col" width="300">價格</th>
        <th scope="col" width="300">庫存</th>
        <th scope="col">操作</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(item, index) in products" :key="item.id">
        <td>
          <span v-if="!item.isEdit">{{ item.name }}</span>
          <input v-else v-model="item.name" />
        </td>
        <td>
          <span v-if="!item.isEdit">
            {{ item.describe }}
          </span>
          <input v-else v-model="item.describe" />
        </td>
        <td>
          <span v-if="!item.isEdit">{{ item.price }}</span>
          <input v-else v-model="item.price" />
        </td>
        <td>
          <button class="btn btn-primary me-2 px-3" @click="item.stock--">-</button>
          {{ item.stock }}
          <button class="btn btn-primary ms-2 px-3" @click="item.stock++">+</button>
        </td>
        <td>
          <button class="btn btn-warning" v-if="!item.isEdit" @click="editItem(index)">編輯</button>
          <button class="btn btn-danger" v-else @click="checkItem(index)">確認</button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script setup>
import { ref } from 'vue'

const products = ref([
  {
    id: '1',
    name: '珍珠奶茶',
    describe: '香濃奶茶搭配 QQ 珍珠',
    price: '50',
    stock: '20',
    isEdit: false
  },
  {
    id: '2',
    name: '冬瓜檸檬',
    describe: '清新冬瓜配上新鮮檸檬',
    price: '45',
    stock: '18',
    isEdit: false
  },
  {
    id: '3',
    name: '翡翠檸檬',
    describe: '綠茶與檸檬的完美結合',
    price: '55',
    stock: '34',
    isEdit: false
  },
  {
    id: '4',
    name: '四季春茶',
    describe: '香醇四季春茶，回甘無比',
    price: '45',
    stock: '10',
    isEdit: false
  },
  {
    id: '5',
    name: '阿薩姆奶茶',
    describe: '阿薩姆紅茶搭配香醇鮮奶',
    price: '50',
    stock: '25',
    isEdit: false
  },
  {
    id: '6',
    name: '檸檬冰茶',
    describe: '檸檬與冰茶的清新組合',
    price: '45',
    stock: '20',
    isEdit: false
  },
  {
    id: '7',
    name: '芒果綠茶',
    describe: '芒果與綠茶的獨特風味',
    price: '55',
    stock: '18',
    isEdit: false
  },
  {
    id: '8',
    name: '抹茶拿鐵',
    describe: '抹茶與鮮奶的絕配',
    price: '60',
    stock: '20',
    isEdit: false
  }
])

const editItem = (index) => {
  products.value[index].isEdit = true
}

const checkItem = (index) => {
  products.value[index].isEdit = false
}
</script>
