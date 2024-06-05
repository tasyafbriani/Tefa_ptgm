<template>
  <div class="container-fluid p-5">
    <div class="col-lg-12 -flex justify-content-around">
      <div class="my-3">
        <form @submit.prevent="getBooks">
          <input
            v-model="keyword"
            type="search"
            class="form-control rounded-5"
            placeholder="Mau Baca Apa Hari Ini?"
          />
        </form>
      </div>
      <div class="my-4 text-muted">menampilkan {{ books?.length }} dari {{ totalBuku }}</div>
      <div class="row justify-content-evenly">
        <div v-for="(buku, i) in books" :key="i" class="col-lg-2">
          <nuxt-link :to="`/buku/${buku.id}`">
            <div class="card mb-3">
              <div class="card-body">
                <img :src="buku.cover" class="cover" :alt="buku.judul" />
              </div>
            </div>
          </nuxt-link>
        </div>
      </div>
    </div>
  </div>
  <nuxt-link to="/">
    <button type="submit" class="btn ms-3 btn-lg">KEMBALI</button>
  </nuxt-link>
</template>

<script setup>
const supabase = useSupabaseClient();
const totalBuku = ref(0)

const books = ref([]);

const getBooks = async () => {
  const { data, error } = await supabase
    .from("buku")
    .select(`*, kategori(*)`)
    .ilike("judul", `%${keyword.value}%`);
  if (data) books.value = data;
}
const getTotalBuku = async () => {
  const { count, error } = await supabase.from("buku").select("*, kategori(*)", { count: 'exact', head: true });
  if (count) totalBuku.value = count;
};

onMounted(() => {
  getBooks();
  getTotalBuku()
});

const keyword = ref("");
</script>

<style scoped>
.shadow-lg {
  box-shadow: 6px 4px 0 #2e2e2eae !important;
}
.card:hover {
  transform: scale(1.05);
  box-shadow: 4px 4px 20px #2e2e2eae !important;
}
.card {
  transition: all .2s ease-in-out;
}
.card-body{
  width: 100%;
  height: 400px;
  padding: 0;
}
.cover {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: 0 30;
}

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
