<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import axios from 'axios'

const email = ref('')
const password = ref('')
const router = useRouter()

const handleLogin = async () => {
  try {
    const res = await axios.post('http://127.0.0.1:8000/api/auth/login', {
      email: email.value,
      password: password.value
    })

    const token = res.data.token || res.data.access_token

    localStorage.setItem('token', token)

    router.push('/dashboard')
  } catch (err) {
    console.log(err)
    alert('Email atau Password Salah')
  }
}
</script>

<template>
  <div class="login-container">
    <div class="login-box">
      <h2>Login</h2>
      <p>Silahkan Login Terlebih Dahulu</p>

      <form @submit.prevent="handleLogin">
        <div class="input-group">
          <label>Email</label>
          <input type="email" v-model="email" placeholder="Masukkan email" />
        </div>

        <div class="input-group">
          <label>Password</label>
          <input type="password" v-model="password" placeholder="Masukkan password" />
        </div>

        <button @click="handleLogin">Login</button>
        <p>Belum memiliki akun? <router-link to="/register">Daftar</router-link></p>
      </form>
    </div>
  </div>
</template>

<style scoped>
.login-container {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #f5f5f5;
}

.login-box {
  background: white;
  padding: 30px;
  width: 300px;
  border-radius: 12px;
  box-shadow: 0 5px 15px rgba(0,0,0,0.1);
}

.login-box h2 {
  margin-bottom: 5px;
}

.login-box p {
  font-size: 14px;
  margin-bottom: 20px;
  color: #666;
}

.input-group {
  margin-bottom: 15px;
  display: flex;
  flex-direction: column;
}

.input-group label {
  font-size: 13px;
  margin-bottom: 5px;
}

.input-group input {
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 6px;
}

button {
  width: 100%;
  padding: 10px;
  border: none;
  background: #333;
  color: white;
  border-radius: 6px;
  cursor: pointer;
}

button:hover {
  background: #555;
}
</style>