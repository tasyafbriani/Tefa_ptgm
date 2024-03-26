<template>
  <div class="container-fluid p-5">
    <div class="col-lg-12 -flex justify-content-around">
      <h2 class="text-center">Buku</h2>
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
      <div class="my-3 text-muted">Menampilkan 30 dari 30</div>
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

const books = ref([]);

const getBooks = async () => {
  const { data, error } = await supabase
    .from("buku")
    .select(`*, kategori(*)`)
    .ilike("judul", `%${keyword.value}%`);
  if (data) books.value = data;
};

onMounted(() => {
  getBooks();
});

const keyword = ref("");
</script>

<style scoped>
.card-body > img {
  width: 200px;
}

.cover {
  height: 100%;
  object-fit: cover;
  object-position: 0 30;
  border: none;
}
.card {
  border: none;
}

button {
  border: 1px solid #000;
  background-color: #265cb5;
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
