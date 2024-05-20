<template>
    <div class="container-fluid font">
    <div class="row my-5 d-flex justify-content-around">
        <div class="col-lg-6 box">
        <nuxt-link to="/pengunjung/tambah">
            <div class="card bg-pengunjung rounded-5">
            <div class="card-body">
                <h4>Pengunjung</h4>
            </div>
            </div>
        </nuxt-link>
        </div>
        <div class="col-lg-6 box">
        <nuxt-link to="/buku">
            <div class="card bg-buku rounded-5">
            <div class="card-body">
                <h4>Buku</h4>
            </div>
            </div>
        </nuxt-link>
        </div>
    </div>
    <div class="statistik">
        <h1>STATISTIK</h1>
    </div>
    <div class="row my-5 d-flex justify-content-around">
        <div class="col-lg-6 box">
        <nuxt-link to="/pengunjung">
        <div class="card c2 rounded-5">
            <div class="card-body text">
            <h2><span class="no">{{ jml_pengunjung }}</span>Pengunjung</h2>
            </div>
        </div>
        </nuxt-link>
        </div>
        <div class="col-lg-6 box">
        <div class="card c3 rounded-5">
            <div class="card-body text">
            <h2><span class="no">{{ jml_buku }}</span>Buku</h2>
            </div>
        </div>
        </div>
    </div>
    <div class="container">
        <div class="row">
        <statistik />
        </div>
    </div>
    </div>
</template>

<script setup>
useHead({ title: "Home / Perpus Digital" })
const supabase = useSupabaseClient()
const jml_pengunjung = ref(0)
const jml_buku = ref(0)

async function getjml_pengunjung() {
const{ error , data, count } = await supabase
.from("pengunjung")
.select('*', { count: 'exact' })
if (count) jml_pengunjung.value = count

}
async function getjml_buku() {
const{ error , data, count } = await supabase
.from("buku")
.select('*', { count: 'exact' })
if (count) jml_buku.value = count

}

onMounted(() => {
getjml_pengunjung()
getjml_buku()
})
</script>

<style scoped>
.card {
    height: 250px;
    box-shadow: 1px 1px 10px #17161633;
}

.card.bg-pengunjung {
    background-image: url('../assets/img/bg-home-kunjungan.png');
    background-repeat: no-repeat;
    background-position: center center;
    background-size: cover;
}

.card.bg-buku {
    background-image: url('../assets/img/bg-home-cari-buku.png');
    background-repeat: no-repeat;
    background-position: center center;
    background-size: cover;
}

.card-body>h4 {
    color: #000000;
    position: static;
    bottom: 5px;
    right: 15px;
}

.statistik {
    margin-left: 50px;
}

.box {
    width: 45%;
}
.box a {
    text-decoration:none;
}

.c2 {
    border: 1px solid #000;
    background-color:#E1C6F6;
    color:black;
}

.c3 {
    border: 1px solid #000;
    background-color: #B7E9F3;
}

.text {
    display: flex;
    justify-content: center;
    align-items: center;
}

.no {
    font-size: 70px;
}
</style>

