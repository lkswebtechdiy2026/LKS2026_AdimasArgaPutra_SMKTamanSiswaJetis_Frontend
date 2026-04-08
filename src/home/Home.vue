<script setup>
import { RouterView } from 'vue-router';

</script>

<template>
  <div class="container">
    
    <header class="navbar">
      <h1>UMKM</h1>
      <nav>
        <a href="#">Home</a>
        <a href="#">Fitur</a>
        <a href="#">Tentang</a>
        <router-link to="/login">Login</router-link>
      </nav>
    </header>

    <section class="hero">
      <div class="hero-text">
        <h2>
          Pembiayaan dan manajemen UMKM menjadi mudah
        </h2>
        <p>
          Solusi digital untuk membantu pelaku UMKM mengelola usaha,
          keuangan, dan perkembangan bisnis dalam satu sistem.
        </p>
      </div>
    </section>

    <section class="fitur">
      <h3>Fitur Unggulan</h3>

      <div class="card-group">
        <div class="card">
          <h4>Manajemen Keuangan</h4>
          <p>Mencatat pemasukan dan pengeluaran dengan mudah.</p>
        </div>

        <div class="card">
          <h4>Pembiayaan</h4>
          <p>Akses pembiayaan UMKM secara cepat dan aman.</p>
        </div>

        <div class="card">
          <h4>Laporan Otomatis</h4>
          <p>Data usaha tersusun rapi dan siap dianalisis.</p>
        </div>
      </div>
    </section>

  </div>
</template>

<style scoped>
.container {
  font-family: Arial, sans-serif;
}

.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #aef3f3;
  padding: 15px 40px;
  border-radius: 0 0 20px 20px;
}

.navbar h1 {
  font-size: 20px;
}

.navbar nav a {
  margin-left: 20px;
  text-decoration: none;
  color: #333;
}

.navbar .btn {
  background: #333;
  color: white;
  padding: 6px 12px;
  border-radius: 8px;
}

.hero {
  padding: 80px 40px;
  background: #fff5e6;
  text-align: center;
}

.hero h2 {
  font-size: 32px;
  margin-bottom: 10px;
}

.hero p {
  max-width: 600px;
  margin: auto;
  margin-bottom: 20px;
}

.hero button {
  padding: 10px 20px;
  border: none;
  background: #333;
  color: white;
  border-radius: 8px;
  cursor: pointer;
}

.fitur {
  padding: 50px 40px;
  text-align: center;
}

.card-group {
  display: flex;
  gap: 20px;
  justify-content: center;
  margin-top: 20px;
}

.card {
  background: #f4f4f4;
  padding: 20px;
  border-radius: 15px;
  width: 250px;
  text-align: left;
  transition: 0.3s;
}

.card:hover {
  transform: translateY(-5px);
}
</style>