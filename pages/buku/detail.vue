<template>
    <div class="d-flex justify-content-around m-5">
    <div class="p-5">
        <img src="~/assets/img/book1.jpg" class="cover">
    </div>
    <div class="p-5">
        <p>Judul : I'M CAREL</p>
        <p>Penulis : Septiana</p>
        <p>Penerbit: Sunset Road</p>
        <p>Tahun terbit: 2023</p>
        <p>Sinopsis : Jika biasanya geng motor terkenal dengan anggotanya yang urakan,biang masalah,tawuran sana sini,suka berbuat onar.namun,berbeda dengan geng motor yang satu ini,Battara Geng.Geng Motor yang diketuai oleh Carel Aldeguer Ghazali.Remaja tapan,putra pembalap ternama sekaligus pemilik pondok pesantren.Jika geng lain memiliki bascamp tersendiri untuk nongkrong,maka Battra Geng berbeda,mereka akan nongkrong di pondok pesantren milik ibu sang ketua.'aaa carel,pacaran yuk..' pria yang merasa namanya di panggil itu menoleh,'pacaran sama malaikat izrail mau?'</p>
        <p>Kategori : Novel</p>
        <p>Rak : 2</p>
    </div>
    </div>
    <nuxt-link to="/buku/">
    <button type="submit" class="btn ms-3 btn-lg">KEMBALI</button>
    </nuxt-link>
</template>

<style scoped>
button {
    border: 1px solid #000;
    background-color: #265CB5;
    color: #fff;
    position: fixed;
    bottom: 30px;
    right: 30px;
    border-radius: 20px;
}

button:hover {
    border: 1px solid #000;
    background-color: #fff;
    color: #265CB5;
}
</style>