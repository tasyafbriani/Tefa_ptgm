<template>
    <div class="container-fluid">
    <div class="row">
        <div class="col-lg-12">
        <h2 class="text-center my-4">RIWAYAT KUNJUNGAN</h2>
        <div class="my-3">
            <form  @submit.prevent="getBuku">
            <input v-model="keyword" type="search" class="form-control rounded-5" placeholder="Filter...">
            </form>
        </div>
        <div class="my-3 text-muted">menampilkan daftar pengunjung</div>
        <table class="table table-bordered">
            <thead>
            <tr>
            <td>NO</td>
            <td>NAMA</td>
            <td>KEANGGOTAAN</td>
            <td>WAKTU</td>
            <td>KEPERLUAN</td>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(visitor, i) in visitors" :key="i">
            <td>{{ i + 1 }}.</td>
            <td>{{ visitor.nama }}</td>
            <td>{{ visitor.keanggotaan.nama }}</td>
            <td>{{ visitor.tanggal }}, {{ visitor.waktu }}</td>
            <td>{{ visitor.keperluan.nama }}</td>
            </tr>
        </tbody>
        </table>
    </div>
    </div>
    <nuxt-link to="/pengunjung/tambah">
    <button type="submit" class="btn ms-3 btn-lg">KEMBALI</button>
    </nuxt-link>
</div>
</template>

<script setup>
const supabase = useSupabaseClient()
const keyword = ref('')
const visitors = ref([])

const getPengunjung = async () => {
const { data, error } = await supabase.from('pengunjung').select(`*, keanggotaan(*), keperluan(*)`)
if(data) visitors.value = data
}
const getBuku = async () => {
const { data, error } = await supabase.from('pengunjung').select(`*, keanggotaan(*), keperluan(*)`)
.ilike('nama', `%${keyword.value}%`)
if(data) visitors.value = data
}

onMounted(() => {
getPengunjung()
getBuku()
})
</script>

<style scoped>
button {
border: 1px solid #000;
background-color: #D3D3D3;
color: #fff;
position: fixed;
bottom: 30px;
right: 30px;
border-radius: 20px;
}

button:hover {
border: 1px solid #000;
background-color: #fff;
color: #265cb5;
}
.my-3 input {
background-color: #f3f3f3;
}


</style>
