<template>
    <h2 class="text-start my-4">{{ buku.judul }}</h2>
    <span v-if="buku.cover"><img :src="buku.cover" :alt="buku.judul"></span>
    <span v-else><img src="https://www.google.com/url?sa=i&url=https%3A%2F%2Fen.m.wikipedia.org%2Fwiki%2FFile%3APlaceholder_view_vector.svg&psig=AOvVaw2flwzLHayqCCqqbxU2I7U-&ust=1711438058162000&source=images&cd=vfe&opi=89978449&ved=0CBAQjRxqFwoTCLCG_ePxjoUDFQAAAAAdAAAAABAH" :alt="buku.judul"></span>
    <div class="row mt-5">
        <div class="col-md-3 card">
            <img :src="buku.cover" class="cover" alt="cover buku">
        </div>
        <div class="p-5 col-md-9">
            <div class="badge bg-primary p-2">{{ buku.kategori }}</div>
            <ul class="text">
                <li class="list-group-item">Judul: {{ buku.judul }}</li>
                <li class="list-group-item">Penulis: {{ buku.penulis }}</li>
                <li class="list-group-item">Penerbit: {{ buku.penerbit }}</li> 
                <li class="list-group-item">Tahun Penerbit: {{ buku.tahun_penerbit }}</li> 
                <li class="list-group-item">Deskripsi: {{ buku.deskripsi }}</li> 
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
