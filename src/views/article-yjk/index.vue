<template>
  <h1>yjk</h1>
  <div>
    <el-button @click="handleLogin">登录</el-button>
    <el-button @click="handleProfile">个人信息</el-button>
  </div>
</template>

<script setup>
import axios from 'axios'
import store from '@/store'

const handleLogin = () => {
  axios
    .post(
      'https://api.imooc-admin.lgdsunday.club/api/sys/login',
      {
        username: 'admin',
        password: 'e10adc3949ba59abbe56e057f20f883e'
      },
      {
        headers: {
          icode: '1FD4049CF08AA041'
        }
      }
    )
    .then((res) => {
      console.log(res)
    })
}

const handleProfile = () => {
  axios
    .get('https://api.imooc-admin.lgdsunday.club/api/sys/profile', {
      headers: {
        icode: '1FD4049CF08AA041',
        Authorization: `Bearer ${store.getters.token}`
      }
    })
    .then((res) => {
      console.log(res)
    })
}
</script>

<style scoped>
</style>
