<script setup>
import { onMounted, ref } from 'vue'
import { useRouter } from 'vue-router'
import axios from 'axios'

const user = ref(null)
const router = useRouter()

onMounted(async () => {
  try {
    const token = localStorage.getItem('token')

    const res = await axios.get('http://127.0.0.1:8000/api/users', {
      headers: {
        Authorization: `Bearer ${token}`
      }
    })

    user.value = res.data
  } catch (err) {
    console.log(err)
  }
})

const logout = () => {
  localStorage.removeItem('token')
  router.push('/login')
}
</script>

<template>
  <div class="wrapper">
    <header class="topbar">
      <h2>Dashboard</h2>
      <button @click="logout">Logout</button>
    </header>

    <div class="content">
      <div class="card">
        <h3 v-if="user">Halo</h3>
        <p v-if="user">Selamat datang</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.wrapper {
  min-height: 100vh;
  background: #f6f7fb;
  font-family: Arial, sans-serif;
}

.topbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 40px;
  background: white;
  box-shadow: 0 2px 10px rgba(0,0,0,0.05);
}

.topbar h2 {
  font-size: 20px;
}

.topbar button {
  padding: 8px 14px;
  background: #222;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}

.content {
  padding: 30px 40px;
}

.card {
  background: white;
  padding: 25px;
  border-radius: 12px;
  margin-bottom: 20px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.05);
}

.grid {
  display: flex;
  gap: 20px;
}

.box {
  flex: 1;
  background: white;
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.05);
}

.box h4 {
  font-size: 14px;
  color: #666;
  margin-bottom: 8px;
}

.box span {
  font-size: 18px;
  font-weight: bold;
}
</style>