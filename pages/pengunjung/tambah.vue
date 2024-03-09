<template>
    <div class="container-fluid p-5">
    <div class="row">
        <div class="col-lg-12">
        <h2 class="text-center my-4">FORM KUNJUNGAN</h2>
        <form>
            <div class="mb-3">
            <input type="text" class="form-control form-control-lg radius" placeholder="Nama...">
            </div>
            <div class="mb-3">
            <select class="form-control form-control-lg form-select radius">
                <option value="">Keanggotaan</option>
                <option value="Siswa">Siswa</option>
                <option value="Guru">Guru</option>
                <option value="Staf">Staf</option>
                <option value="Umum">Umum</option>
            </select>
            </div>
            <div class="mb-3">
            <div class="row">
                <div class="col-md-4">
                <select class="form-control form-control-lg form-select radius mb-2">
                    <option value="">Tingkat</option>
                    <option value="X">X</option>
                    <option value="XI">XI</option>
                    <option value="XII">XII</option>
                </select>
                </div>            
                <div class="col-md-4">
                <select class="form-control form-control-lg form-select radius mb-2">
                    <option value="">Jurusan</option>
                    <option value="PPLG">PPLG</option>
                    <option value="TJKT">TJKT</option>
                    <option value="TSM">TSM</option>
                    <option value="DKV">DKV</option>
                    <option value="TOI">TOI</option>
                </select>
                </div>
                <div class="col-md-4">
                <select class="form-control form-control-lg form-select radius mb-2">
                    <option value="">Kelas</option>
                    <option value="1">1</option>
                    <option value="2">2</option>
                    <option value="3">3</option>
                    <option value="4">4</option>
                </select>
                </div>
            </div>
            </div>
            <div class="mb-3">
            <select class="form-control form-control-lg form-select radius">
                <option value="">Keperluan</option>
                <option value="Baca Buku">Baca Buku</option>
                <option value="Pinjam Buku">Pinjam Buku</option>
                <option value="Kembalikan Buku">Kembalikan Buku</option>
            </select>
            </div>
            <div class="tombol">
            <nuxt-link to="/pengunjung/">
                <button type="submit" class="btn btn-lg radius">KIRIM</button>
            </nuxt-link>
            <nuxt-link to="/">
                <button type="submit" class="btn btn-lg radius kembali">KEMBALI</button>
            </nuxt-link>
            </div>
        </form>
        </div>
    </div>
    </div>
</template>

<style scoped>
.radius {
    border-radius: 10px;
    background-color: #f3f3f3;
}

input {
    border: 1px solid #000;
    height:42px;
}

select {
    border: 1px solid #000;  
}

button {
    border: 1px solid #000;
    background-color: #265CB5;
    color: #fff;
}

button:hover {
    border: 1px solid #000;
    background-color: #fff;
    color: #265CB5;
}

.kembali {
    position: fixed;
    bottom: 30px;
    right: 30px;
    border-radius: 20px;
}
</style>