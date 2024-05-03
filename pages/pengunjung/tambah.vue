<template>
  <div class="container-fluid p-5">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">FORM KUNJUNGAN</h2>
        <form @submit.prevent="kirimData">
          <div class="mb-3">
            <input
              v-model="form.nama"
              type="text"
              class="form-control form-control-lg radius"
              placeholder="Nama..."
            />
          </div>
          <div class="mb-3">
            <select
              v-model="form.keanggotaan"
              class="keanggotaan form-control form-select rounded-5"
            >
              <option value="">Keanggotaan</option>
              <option
                v-for="(member, i) in members"
                :key="i"
                :value="member.id"
              >
                {{ member.nama }}
              </option>
            </select>
          </div>
          <div v-if="form.keanggotaan == 1" class="mb-3">
            <div class="row">
              <div class="col-md-4">
                <select
                  v-model="form.tingkat"
                  class="tingkat form-control form-control-lg form-select radius mb-2"
                >
                  <option value="">Tingkat</option>
                  <option value="X">X</option>
                  <option value="XI">XI</option>
                  <option value="XII">XII</option>
                </select>
              </div>
              <div class="col-md-4">
                <select
                  v-model="form.jurusan"
                  class="jurusan form-control form-control-lg form-select radius mb-2"
                >
                  <option value="">Jurusan</option>
                  <option value="PPLG">PPLG</option>
                  <option value="TJKT">TJKT</option>
                  <option value="TSM">TSM</option>
                  <option value="DKV">DKV</option>
                  <option value="TOI">TOI</option>
                </select>
              </div>
              <div class="col-md-4">
                <select
                  v-model="form.kelas"
                  class="kelas form-control form-control-lg form-select radius mb-2"
                >
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
            <select
              v-model="form.keperluan"
              class="keperluan form-control form-control-lg form-select radius"
            >
              <option value="">Keperluan</option>
              <option v-for="(item, i) in objectives" :key="i" :value="item.id">
                {{ item.nama }}
              </option>
            </select>
          </div>
          <button type="submit" class="btn btn-lg radius">KIRIM</button>
          <div class="tombol">
            <nuxt-link to="/" class="btn btn-lg radius kembali">
              KEMBALI
            </nuxt-link>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient();

const members = ref([]);
const objectives = ref([]);

const form = ref({
  nama: "",
  keanggotaan: "",
  tingkat: "",
  jurusan: "",
  kelas: "",
  keperluan: "",
});

const kirimData = async () => {
  //   console.log(form.value);
  const { error } = await supabase.from("pengunjung").insert([form.value]);
  if (!error) navigateTo("/pengunjung");
};

const getKeanggotaan = async () => {
  const { data, error } = await supabase.from("keanggotaan").select("*");
  if (data) members.value = data;
};

const getKeperluan = async () => {
  const { data, error } = await supabase.from("keperluan").select("*");
  if (data) objectives.value = data;
};

onMounted(() => {
  getKeanggotaan();
  getKeperluan();
});
</script>

<style scoped>
.radius {
  border-radius: 10px;
  background-color: #f3f3f3;
}

input {
  border: 1px solid #000;
  height: 42px;
}

select {
  border: 1px solid #000;
}

button {
  border: 1px solid #000;
  background-color: #265cb5;
  color: #265cb5;
}

button:hover {
  border: 1px solid #000;
  background-color: #fff;
  color: #265cb5;
}

.kembali {
  background-color: #D3D3D3;
  position: fixed;
  bottom: 30px;
  right: 30px;
  border-radius: 20px;
}
</style>
