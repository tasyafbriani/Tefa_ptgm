<template>
<div>
    <h2 class="text-start my-4">{{ buku.judul}}</h2>
    <div class="row">
    <div class="col-md-2">
    <span v-if="buku.cover"><img :src="buku.cover" :alt="buku.judul"></span>
    <span v-else><img src="https://www.google.com/url?sa=i&url=https%3A%2F%2Fen.m.wikipedia.org%2Fwiki%2FFile%3APlaceholder_view_vector.svg&psig=AOvVaw2flwzLHayqCCqqbxU2I7U-&ust=1711438058162000&source=images&cd=vfe&opi=89978449&ved=0CBAQjRxqFwoTCLCG_ePxjoUDFQAAAAAdAAAAABAH" :alt="buku.judul"></span>
</div>
    <div class="col-md-6">
        <ul class="list-group list-group-flush">
            <li class="list-group-item">penulis : {{ buku.penulis }}</li>
            <li class="list-group-item">tahun terbit : {{ buku.tahun_terbit}}</li>
            <li class="list-group-item">penerbit : {{ buku.penerbit }}</li>
            <li class="list-group-item">rak : {{ buku.rak}}</li>
            <li class="list-group-item">deskripsi : {{ buku.deskripsi }}</li>
        </ul>
    </div>
</div>  
</div>  
</template>

<script setup>
const supabase = useSupabaseClient()

const route = useRoute()
const buku = ref([])

const getBookById = async () => {
    const { data, error } = await supabase.from('buku').select(`*, kategori(*)`)
    .eq('id', route.params.id)
    if(data) buku.value = data[0]
}

onMounted(() =>{
    getBookById()
})
</script>

