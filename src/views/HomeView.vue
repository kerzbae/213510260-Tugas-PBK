<template>
  <div>
    <h1>Daftar Kegiatan</h1>
    <form @submit.prevent="addKegiatan">
      <input v-model="kegiatan" placeholder="Tambah kegiatan baru...">
      <button type="submit">Tambah</button>
    </form>
    <ul>
      <li v-for="(kegiatan, index) in kegiatanList" :key="index">
        <input type="checkbox" :checked="kegiatan.done" @change="toggleDone(index)">
        <span :class="{ 'done': kegiatan.done }">{{ kegiatan.teks }}</span>
        <button @click="removeKegiatan(index)">Hapus</button>
      </li>
    </ul>
    <button @click="showAll">Show All</button>
    <button @click="showUndone">Show Not Done</button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      kegiatan: '',
      kegiatanList: [

      ]
    }
  },
  methods: {
    addKegiatan() {
      if (this.kegiatan.trim()) {
        this.kegiatanList.push({ teks: this.kegiatan, done: false })
        this.kegiatan = ''
      }
    },
    removeKegiatan(index) {
      this.kegiatanList.splice(index, 1)
    },
    toggleDone(index) {
      this.kegiatanList[index].done = !this.kegiatanList[index].done
    },
    showAll() {
      this.kegiatanList.forEach(kegiatan => kegiatan.tampil = true)
    },
    showUndone() {
      this.kegiatanList.forEach(kegiatan => kegiatan.tampil = !kegiatan.done)
    }
  }
}
</script>

<style>
h1 {
  text-align: center;
  font-size: 36px;
  margin-top: 50px;
}

form {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}

input[type="text"] {
  padding: 8px;
  font-size: 18px;
  border: none;
  border-radius: 5px;
  margin-right: 10px;
}

button[type="submit"] {
  padding: 8px 16px;
  font-size: 18px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

li {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}

input[type="checkbox"] {
  margin-right: 10px;
}

span {
  font-size: 20px;
}

button {
  padding: 8px 16px;
  font-size: 16px;
  background-color: #f44336;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin-left: 10px;
}

button:hover {
  background-color: #ff0000;
}

button:focus {
  outline: none;
}

button:active {
  transform: translateY(1px);
}

.done {
  text-decoration: line-through;
  color: #999;
}

li {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 10px;
  text-align: center;
}

body{
  background-color: wheat;
}

nav a.router-link-exact-active {
  color: #fc0047;
}

</style>