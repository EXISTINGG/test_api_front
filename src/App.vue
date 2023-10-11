<template>
  <el-alert :title="`服务器地址：${url}`" type="success" :closable="false" />
  <el-table :data="tableData" style="width: 100%">
    <el-table-column prop="name" label="姓名" width="180" />
    <el-table-column prop="age" label="年龄" width="180" />
    <el-table-column prop="gender" label="性别" />
  </el-table>
</template>

<script setup>
import axios from 'axios'
import { ref, onMounted } from 'vue'

const tableData = ref([])
const url = ref('https://koaapi.hxq-001.top')

const initData = async () => {
  const { data } = await axios.get(url.value);

  tableData.value = data.data;
}

onMounted(() => initData())
</script>
